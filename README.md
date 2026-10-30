# imgauth — API di attestazione opere digitali

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Digital-work attestation and proof-of-existence service operated by Spazio Genesi ETS, an Italian non-profit (third-sector entity). The client computes a SHA-256 fingerprint locally and sends only the 64-hex hash — file bytes never leave the device. The service binds that fingerprint to a signed server-side timestamp (HMAC), issues a PAdES B-LT signed PDF certificate carrying an RFC 3161 timestamp from an Adobe AATL-recognised TSA, and anchors the fingerprint in Bitcoin through OpenTimestamps across four independent calendars. Verification is free and unlimited for anyone, and the proof of existence never expires. Exposes an 18-operation public REST API (OpenAPI 3.0.3, served at the API host root), a hosted zero-install remote MCP server whose eight tools answer tools/list anonymously, an sg-attest CLI, a GitHub Action, embeddable SVG badges and three CORS-open public status endpoints. The API contract is in Italian by design. Positioned explicitly as a NON-QUALIFIED attestation under eIDAS 2.0.

**Areas:** digital notarization · Timestamping · proof-of-existence · Content Authenticity · Provenance · Copyright · IP protection · Blockchain · Bitcoin · OpenTimestamps · Security · Documents

## imgauth — API di attestazione opere digitali on APIs.io

Everything profiled for imgauth — API di attestazione opere digitali is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/imgauth-api-di-attestazione-opere-digitali/](https://apis.io/providers/imgauth-api-di-attestazione-opere-digitali/)** — or go straight to one of the APIs or properties below.

### APIs (15)

- [imgauth Remote MCP Server](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-remote-mcp-server/) — Hosted, zero-install MCP server (Streamable HTTP, protocol 2025-06-18) exposing the attestation service to MCP-capable agents. The eight tools were read…
- [imgauth — API di attestazione opere digitali Agent API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-agent-api/) — The Agent API from imgauth — API di attestazione opere digitali — 4 operation(s) for agent.
- [imgauth — API di attestazione opere digitali Badge API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-badge-api/) — The Badge API from imgauth — API di attestazione opere digitali — 2 operation(s) for badge.
- [imgauth — API di attestazione opere digitali C API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-c-api/) — The C API from imgauth — API di attestazione opere digitali — 1 operation(s) for c.
- [imgauth — API di attestazione opere digitali Cert API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-cert-api/) — The Cert API from imgauth — API di attestazione opere digitali — 1 operation(s) for cert.
- [imgauth — API di attestazione opere digitali Cert Pdf API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-cert-pdf-api/) — The Cert Pdf API from imgauth — API di attestazione opere digitali — 1 operation(s) for cert pdf.
- [imgauth — API di attestazione opere digitali Hash API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-hash-api/) — The Hash API from imgauth — API di attestazione opere digitali — 1 operation(s) for hash.
- [imgauth — API di attestazione opere digitali Health Log API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-health-log-api/) — The Health Log API from imgauth — API di attestazione opere digitali — 1 operation(s) for health log.
- [imgauth — API di attestazione opere digitali Integrations API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-integrations-api/) — The Integrations API from imgauth — API di attestazione opere digitali — 1 operation(s) for integrations.
- [imgauth — API di attestazione opere digitali Integrazioni API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-integrazioni-api/) — The Integrazioni API from imgauth — API di attestazione opere digitali — 1 operation(s) for integrazioni.
- [imgauth — API di attestazione opere digitali Ots API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-ots-api/) — The Ots API from imgauth — API di attestazione opere digitali — 1 operation(s) for ots.
- [imgauth — API di attestazione opere digitali Ping API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-ping-api/) — The Ping API from imgauth — API di attestazione opere digitali — 1 operation(s) for ping.
- [imgauth — API di attestazione opere digitali Status API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-status-api/) — The Status API from imgauth — API di attestazione opere digitali — 1 operation(s) for status.
- [imgauth — API di attestazione opere digitali Status History API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-status-history-api/) — The Status History API from imgauth — API di attestazione opere digitali — 1 operation(s) for status history.
- [imgauth — API di attestazione opere digitali Verify API](https://apis.io/apis/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-verify-api/) — The Verify API from imgauth — API di attestazione opere digitali — 1 operation(s) for verify.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [mcp](https://apis.io/servers/imgauth-api-di-attestazione-opere-digitali/mcp/)

#### Collections (1)

Postman and Open Collection request collections.

- [imgauth — API di attestazione opere digitali](https://apis.io/collections/imgauth-api-di-attestazione-opere-digitali/open-imgauth-api-di-attestazione-opere-digitali-openapi-original/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Imgauth Api Di Attestazione Opere Digitali Openapi Overlay](https://apis.io/overlays/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-openapi-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Imgauth Api Di Attestazione Opere Digitali Authentication](https://apis.io/security/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-authentication/)
- [Imgauth Api Di Attestazione Opere Digitali Domain Security](https://apis.io/security/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-domain-security/)
- [Imgauth Api Di Attestazione Opere Digitali Trust Center](https://apis.io/security/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-trust-center/)
- [Imgauth Api Di Attestazione Opere Digitali Vulnerability Disclosure](https://apis.io/security/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Imgauth Api Di Attestazione Opere Digitali Plans Pricing](https://apis.io/plans/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Imgauth Api Di Attestazione Opere Digitali Rate Limits](https://apis.io/rate-limits/imgauth-api-di-attestazione-opere-digitali/imgauth-api-di-attestazione-opere-digitali-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.spaziogenesi.org/)
- [Documentation](https://attestazione.spaziogenesi.org/en/developer/)
- [Getting started](https://attestazione.spaziogenesi.org/en/developer/keys/)
- [API reference](https://attestazione.spaziogenesi.org/docs/)
- [Pricing](https://attestazione.spaziogenesi.org/professionale/)
- [Sign up](https://attestazione.spaziogenesi.org/en/developer/keys/)
- [Changelog](https://attestazione.spaziogenesi.org/changelog/)
- [Blog](https://spaziogenesi.org/news/)
- [Security](https://attestazione.spaziogenesi.org/sicurezza/)
- [Compliance](https://trust.spaziogenesi.org/)
- [Terms of service](https://attestazione.spaziogenesi.org/en/condizioni/)
- [Privacy policy](https://attestazione.spaziogenesi.org/en/privacy.html)
- [GitHub](https://github.com/SPAZIO-GENESI)
- [Status](https://attestazione.spaziogenesi.org/status/)

## API Evangelist rating

**Kin Score 66.3** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 68.3 |
| Contract quality | 47.9 |
| Contract governance | 18.2 |
| Operational transparency | 76.3 |
| Developer ergonomics | 73.2 |
| Access clarity | 92.1 |

**Agent readiness 35.9** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 35.3** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/imgauth-api-di-attestazione-opere-digitali/](https://apis.io/providers/imgauth-api-di-attestazione-opere-digitali/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for imgauth — API di attestazione opere digitali: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/imgauth-api-di-attestazione-opere-digitali/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
