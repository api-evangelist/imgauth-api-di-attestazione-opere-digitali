---
name: Verify an attested work and its Bitcoin anchor
description: >-
  Confirm that a certificate is authentic, that a file really matches its fingerprint, and that the
  proof is anchored in Bitcoin. Needs no credential and costs nothing.
api: openapi/imgauth-api-di-attestazione-opere-digitali-openapi-original.json
mcp: https://attest-mcp-remote.it-e3f.workers.dev/mcp
operations:
  - 'POST /api/verify'
  - 'GET /api/cert'
  - 'GET /api/ots'
  - 'GET /c/{hash}'
tools: [verify_attestation, lookup_certificate, check_anchor]
generated: '2026-08-11'
method: generated
source: >-
  openapi/imgauth-api-di-attestazione-opere-digitali-openapi-original.json and the live MCP tools/list
  at https://attest-mcp-remote.it-e3f.workers.dev/mcp
---

# Verify an attested work

Verification is anonymous, free and unlimited at every tier. Send no credential. Base URL:
`https://imgauth.spaziogenesi.org`.

## The two halves are separate — do both

An attestation proves two different things, checked in two different places, and conflating them is the
most common way to report a false result.

1. **Does the file match the fingerprint?** Re-hash the file **locally** and compare strings. The server
   cannot do this for you on the agent path — it never receives the file.
2. **Is the attestation authentic?** `POST /api/verify` (MCP: `verify_attestation`) checks the server
   HMAC over `attestazione` + bound metadata.

`verify_attestation` checks the **signature only**. Reporting "verified" from it alone, without the local
re-hash, tells the user something you did not check.

## Verify the signature

`POST /api/verify` requires `sha256`, `attestazione` and `hmac`, exactly as printed on the certificate.
The `attestazione` string has the form `SHA-256:<hash>@<ISO timestamp>Z`; the `hmac` is base64, 44
characters, ending in `=`.

If the certificate shows `titolo`, `autore`, `anno` or `note`, you **must** pass every one of them
byte-identically — they are bound into the signature, and a missing or reworded field fails verification
even though the certificate is genuine. If verification fails, check this before telling the user their
certificate is invalid.

The response gives `hash_dichiarato`, `hash_calcolato`, `coincide` and `hmac_valido`. `coincide` is
populated only when the original file was supplied over the multipart path (browsers) — on the agent
path, `hmac_valido` is your answer and `coincide` is yours to establish locally.

## Look up the archive

`GET /api/cert?hash=<sha256>` (MCP: `lookup_certificate`) returns the archived PDF, and
`https://imgauth.spaziogenesi.org/c/<sha256>` is the permanent public certificate page.

A `404` means "not in the archive" — it does **not** mean the attestation was forged. It may simply have
passed its tier retention window (6 months base, 12 months developer, 5 years professional), or never had
a PDF issued at all. Say which.

Trust model worth stating to the user: anyone who knows the fingerprint can retrieve the certificate.
The hash is the only access control.

## Check the Bitcoin anchor

`GET /api/ots?hash=<sha256>` (MCP: `check_anchor`) returns the OpenTimestamps `.ots` proof. The anchor is
created at attestation time and matures from pending to Bitcoin-confirmed within a few hours across four
independent calendars. **Pending is not failure.** A `404` means no proof exists for that fingerprint.

## What you must not overclaim

- The attestation proves the fingerprint existed at a time. It does **not** prove authorship — the
  metadata is self-declared.
- This is an explicitly **non-qualified** attestation under eIDAS 2.0: an advanced electronic signature
  with a self-signed certificate, plus an RFC 3161 timestamp and a Bitcoin anchor. It is not a qualified
  trust service. The provider states this plainly and so should you.

## Errors

`{"error": "<string>"}` on every failure. `400` malformed hash, `404` proof or certificate absent,
`429` per-IP rate limit (60/60s, no `Retry-After` header). Check `GET /api/status` if things look broken:
it reports `worker`, `archive`, `signer` and `anchor` independently, so you can tell the user *which*
component is degraded.
