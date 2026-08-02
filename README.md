# Connecteam

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
