---
name: Subscribe to Connecteam webhooks
description: Register, verify, update and retire webhook subscriptions across all six feature types, and consume the 41 declared events safely.
api: openapi/connecteam-openapi-original.json
generated: '2026-08-01'
method: generated
source: openapi/connecteam-openapi-original.json + https://developer.connecteam.com/docs/setting-up-webhook-via-api
operations:
  - create_webhook_settings_v1_webhooks_post
  - get_webhooks_by_type_settings_v1_webhooks_get
  - get_webhook_settings_v1_webhooks__webhookId__get
  - update_webhook_settings_v1_webhooks__webhookId__put
  - delete_webhook_settings_v1_webhooks__webhookId__delete
scopes:
  - settings.read
  - settings.write
  - settings.delete
---

# Subscribe to Connecteam webhooks

Connecteam declares **41 events** natively in its OpenAPI 3.1 document under the top-level `webhooks` key. There is no AsyncAPI document — the OpenAPI and the Guides → Webhooks section are the contract.

## Steps

1. **Create a subscription.** `create_webhook_settings_v1_webhooks_post` (`POST /settings/v1/webhooks`):

   | Field | Required | Notes |
   |---|---|---|
   | `name` | yes | descriptive label |
   | `url` | yes | HTTPS endpoint |
   | `featureType` | yes | `users`, `forms`, `time_activity`, `shift_scheduler`, `tasks`, `chat` (Beta) |
   | `objectId` | conditional | required for every type **except** `users` |
   | `eventTypes` | yes | array of event names for that feature type |
   | `isDisabled` | no | create in a disabled state |
   | `secretKey` | no | signature-verification secret — **settable only via the API, not in the UI** |

   Always set `secretKey` at creation. It is the only way to authenticate inbound deliveries, and it cannot be added from the dashboard afterwards.

2. **Verify.** `get_webhooks_by_type_settings_v1_webhooks_get` to list, `get_webhook_settings_v1_webhooks__webhookId__get` to read one back.
3. **Amend.** `update_webhook_settings_v1_webhooks__webhookId__put` — use `isDisabled` to pause a noisy subscription rather than deleting and recreating it.
4. **Retire.** `delete_webhook_settings_v1_webhooks__webhookId__delete`.

## Event families

| featureType | events | examples |
|---|---|---|
| `time_activity` | 17 | clock in, clock out, auto clock out, admin add/edit/delete, admin- and auto-approved add/edit/delete requests, geofence and NFC exception approvals, admin declined request |
| `users` | 9 | user created, updated, deleted, archived, restored, promoted, demoted, manager field updated, pending user request fulfilled |
| `chat` (Beta) | 6 | message created/updated/deleted, conversation created/updated/deleted |
| `shift_scheduler` | 5 | shifts created, updated, deleted; availability status created, deleted |
| `forms` | 2 | form submission, form submission edited |
| `tasks` | 2 | task published, task completed |

The full derived catalog with per-event payload schemas is `asyncapi/connecteam-events-webhooks.yml`.

## Rules

- **Shift events are versioned.** V1 (default) emits one event per user assignment; V2 aggregates a shift's assignments into a single event with a base shift id, and turns "add a user to an existing shift" into `shift.updated` rather than `shift.created`. V2 must be enabled per account by Connecteam. Handle both shapes if you cannot confirm which is active.
- **`chat` is Beta.** Per the Beta contract, its payload schema, event names and availability can change without a deprecation window. Do not put it on a critical path.
- **Verify signatures** using the `secretKey` you supplied. Reject deliveries you cannot verify.
- **Be idempotent on your side.** Connecteam publishes no delivery-ordering or retry guarantees, so treat every delivery as at-least-once and key your handler on the event's object id plus timestamp.
- **Webhooks are the cheap path.** Polling burns the per-account rate budget (100/min on Expert); events do not.

Cross-references: `asyncapi/connecteam-events-webhooks.yml`, `conventions/connecteam-conventions.yml`, `rate-limits/connecteam-rate-limits.yml`.
