# Connecteam

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Connecteam is a mobile-first workforce management platform for deskless and non-desk teams, bundling time clock and GPS timesheets, job scheduling, task boards, digital forms and checklists, chat and company communication, HR onboarding, time off, pay rates and sales data into three purchasable hubs (Operations, Communications, HR & Skills).

- Website — https://connecteam.com/
- Developer portal — https://developer.connecteam.com/
- API reference — https://developer.connecteam.com/reference/
- Status — https://connecteam.statuspage.io/

## API

| | |
|---|---|
| Base URL | `https://api.connecteam.com` (Australia: `https://api-au.connecteam.com`) |
| Contract | OpenAPI 3.1.0, served live at `https://api.connecteam.com/openapi.json` |
| Size | 98 paths, 145 operations, 582 component schemas |
| Auth | `X-API-KEY` header, or OAuth 2.0 client credentials (61 scopes, 24-hour Bearer tokens) |
| Events | 41 webhooks declared natively in the OpenAPI `webhooks` object |
| MCP | `https://developer.connecteam.com/mcp` — 3 spec-explorer tools, anonymous `tools/list` |
| Discovery | `/.well-known/api-catalog` (RFC 9727) and `/llms.txt` on the docs host |
| Access | Expert plan or higher; scoped to the hubs the account has purchased |

## Artifacts

`openapi/` · `authentication/` · `scopes/` · `conventions/` · `errors/` · `data-model/` · `asyncapi/` (webhook catalog) · `mcp/` (server + tool crosswalk) · `skills/` (6 agent skills) · `overlays/` · `conformance/` · `lifecycle/` · `changelog/` · `plans/` · `rate-limits/` · `packages/` · `well-known/` · `llms/` · `security/` · `agentic-access/`

## Notable findings

- The OpenAPI is served from the **API host root**, not the docs host — `developer.connecteam.com/openapi.json` 404s.
- **No first-party SDKs.** The docs state plainly that the SDK offered in the reference sandbox is third-party.
- **No idempotency contract.** Only the lock-days `PUT` documents natural idempotency.
- **No security.txt, disclosure policy or bug bounty** on any host, despite SOC 2 Type 2 / ISO 27001 / HIPAA / PCI DSS certifications on the trust center.
- **No A2A agent card.** `api.connecteam.com` returns HTTP 200 with an HTML shell for every unknown path, which makes naive `/.well-known/*` probes read as false hits.
- Spec gaps: `429` is documented in prose but declared on **0 of 145** operations; `401` on only 1.
