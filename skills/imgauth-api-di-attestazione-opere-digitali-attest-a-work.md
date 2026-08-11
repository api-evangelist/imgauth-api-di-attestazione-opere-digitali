---
name: Attest a digital work and issue its certificate
description: >-
  Bind a SHA-256 fingerprint of a file to a signed server timestamp, then generate the signed,
  Bitcoin-anchored PDF certificate — without ever sending the file anywhere.
api: openapi/imgauth-api-di-attestazione-opere-digitali-openapi-original.json
mcp: https://attest-mcp-remote.it-e3f.workers.dev/mcp
operations:
  - 'POST /api/agent/authorize'
  - 'GET /api/agent/token'
  - 'POST /api/hash'
  - 'POST /api/cert-pdf'
tools: [authorize, complete_authorization, attest_hash, create_certificate_pdf]
generated: '2026-08-11'
method: generated
source: >-
  openapi/imgauth-api-di-attestazione-opere-digitali-openapi-original.json and the live MCP tools/list
  at https://attest-mcp-remote.it-e3f.workers.dev/mcp
---

# Attest a digital work

The contract publishes no `operationId`, so operations are referenced here by method and path — that is
the only stable identifier this spec carries. Base URL: `https://imgauth.spaziogenesi.org`.

## Before anything else: hash locally

Compute the fingerprint yourself and send only the hash.

```
sha256sum <file>          # Linux
shasum -a 256 <file>      # macOS
certutil -hashfile <file> SHA256   # Windows
```

**Never** send file bytes or base64 through a tool argument. The MCP server does not accept files, and
the legacy inline-base64 path on `POST /api/hash` exists only for browsers and is capped at 100 MB.
If you cannot compute a hash locally, stop and point the user at
<https://attestazione.spaziogenesi.org> — hashing happens in their browser there.

## 1. Get a credential

Attestation requires one; verification does not.

- If you already hold a key, send `Authorization: Bearer sg_k_<id>_<secret>` and skip to step 2.
- Otherwise run the device flow. `POST /api/agent/authorize` (MCP: `authorize`) returns `code`,
  `verification_url`, `expires_in` and `interval`. **Give the URL to the human** — they must open it and
  clear an anti-bot challenge; you cannot. Then poll `GET /api/agent/token?code=<code>` (MCP:
  `complete_authorization`) at the returned `interval`.

The session token (`sg_s_…`) is delivered **exactly once**. After the first successful read, later polls
return `status: claimed` and the token is gone. Capture it on the first 200 or the session is lost.
A device-flow session is good for 20 attestations over 24 hours.

## 2. Attest the fingerprint

`POST /api/hash` (MCP: `attest_hash`) with the `sha256` and, optionally, `titolo`, `autore`, `anno`,
`note`.

Those four metadata fields are **normalised and bound into the HMAC signature**. They become immutable —
and they must be resupplied byte-identically to verify later. They remain *self-declared*: they do not
prove authorship, and you should not tell the user they do.

Keep the whole response object. You need `attestazione` and `hmac` from it for the next step. Also read
`fascia` (`base` | `sviluppatore` | `convenzione`) and `fascia_motivo` — if `fascia_motivo` is
`pool_esaurito` or `tetto_individuale`, a convention was silently degraded to `base` and the user's
retention guarantee dropped with it. Say so.

**There is no idempotency key.** Re-posting the same fingerprint issues a *new* attestation with a new
timestamp, and retrieval later resolves the *oldest*. If `POST /api/hash` times out, do not blind-retry —
check with `GET /api/cert?hash=<sha256>` first.

## 3. Issue the certificate PDF

`POST /api/cert-pdf` (MCP: `create_certificate_pdf`) with the full object from step 2 — it must carry
`attestazione` and `hmac`, which are re-verified server-side before signing. The service signs the PDF,
archives it, and anchors the fingerprint in Bitcoin via OpenTimestamps.

This endpoint has the tightest limit in the API: **10 requests / 60s per IP**. Everything else is 60/60s.

## Errors

Every failure returns `{"error": "<string>"}` — one free-text field, Italian, no machine-readable code.
Branch on the status:

| Status | Meaning | What to do |
|---|---|---|
| 400 | missing/malformed field, or `attestazione` inconsistent with `sha256`/`timestamp_iso` | fix the payload; do not retry unchanged |
| 403 | invalid credential, or anti-bot check not passed | re-run the device flow |
| 413 | file too large — legacy inline path only, 100 MB | hash locally instead |
| 429 | per-IP rate limit, or the credential's quota is exhausted | back off; **no `Retry-After` is sent**, so use your own backoff |
| 503 | signing service unavailable (fail-closed) | check `GET /api/status`, retry later |

## Afterwards

The certificate is permanently reachable at `https://imgauth.spaziogenesi.org/c/<sha256>`, the PDF at
`GET /api/cert?hash=<sha256>`, and the anchor proof at `GET /api/ots?hash=<sha256>`. The Bitcoin anchor
matures from pending to confirmed within a few hours — do not report it as failed before then.
Retention of the archived PDF depends on tier (6 months base, 12 months developer, 5 years professional),
but the proof of existence itself never expires.
