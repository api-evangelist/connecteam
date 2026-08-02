---
name: Onboard a new employee into Connecteam
description: Create a user, place them in the right smart group, set their pay rate, assign a time-off policy and hand them an onboarding pack — the full day-one provisioning flow.
api: openapi/connecteam-openapi-original.json
generated: '2026-08-01'
method: generated
source: openapi/connecteam-openapi-original.json + https://developer.connecteam.com/docs/users-overview
operations:
  - get_account_information_me_get
  - get_custom_fields_users_v1_custom_fields_get
  - create_users_users_v1_users_post
  - get_smart_groups_users_v1_smart_groups_get
  - set_pay_rates_pay_rates_v1_pay_rates_put
  - assign_user_to_policy_time_off_v1_time_off_policies__timeOffPolicyId__assignments_put
  - get_packs_onboarding_v1_packs_get
  - create_pack_assignments_onboarding_v1_packs__packId__assignments_post
scopes:
  - account_information.read
  - users.read
  - users.write
  - pay_rates.write
  - time_off.write
  - onboarding.read
  - onboarding.write
---

# Onboard a new employee into Connecteam

Base URL `https://api.connecteam.com` (Australia: `https://api-au.connecteam.com`).

## Authentication

Send `X-API-KEY: <key>` on every request, or exchange OAuth 2.0 client credentials first:

```
POST /oauth/v1/token          # operationId: oauth_token_docs_oauth_v1_token_post
Authorization: Basic base64(client_id:client_secret)
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials
```

The token is a Bearer token valid for 86400 seconds. Renew before expiry — there is no refresh token in the client-credentials flow.

**Entitlement check first.** API access requires the Expert plan or higher, and the key only reaches hubs on an eligible plan. Users, `/me`, attachments and publishers work for any Expert+ account; pay rates, time off and onboarding need the matching hub.

## Steps

1. **Confirm the account and its hubs.** `get_account_information_me_get` (`GET /me`). Read the account id and entitlements before writing anything.
2. **Read the custom-field schema.** `get_custom_fields_users_v1_custom_fields_get` (`GET /users/v1/custom-fields`) and, if you need category grouping, `get_custom_fields_users_v1_custom_field_categories_get`. Connecteam models per-company employee attributes as custom fields, not as a free-form metadata bag — resolve the field ids before you build the create payload.
3. **Create the user.** `create_users_users_v1_users_post` (`POST /users/v1/users`). This is a bulk create — send an array even for one person. **Not idempotent**: Connecteam publishes no `Idempotency-Key` contract, so a retried POST creates duplicates. Before retrying a request whose response you never saw, call `get_users_users_v1_users_get` filtered on the phone number or email and reconcile.
4. **Place them in a smart group.** `get_smart_groups_users_v1_smart_groups_get` to resolve the group, then set the driving custom-field values with `update_custom_fields_users_v1_custom_fields_put` — smart groups are rule-driven, so membership follows the field values rather than a direct add call.
5. **Set the pay rate.** `set_pay_rates_pay_rates_v1_pay_rates_put` (`PUT /pay-rates/v1/pay-rates`) with an effective date. Verify with `get_pay_rates_pay_rates_v1_pay_rates_get`.
6. **Assign a time-off policy.** `get_policy_groups_time_off_v1_policy_types_get` to list policy types, then `assign_user_to_policy_time_off_v1_time_off_policies__timeOffPolicyId__assignments_put`. Seed a starting balance with `put_user_balance_time_off_v1_policy_types__policyTypeId__balances__userId__put` if the policy is not accrual-based.
7. **Assign an onboarding pack.** `get_packs_onboarding_v1_packs_get`, then `create_pack_assignments_onboarding_v1_packs__packId__assignments_post`. Confirm with `get_pack_assignments_onboarding_v1_packs__packId__assignments_get`.
8. **Optionally promote to admin.** `invite_admin_users_v1_admins_post` (`POST /users/v1/admins`).

## Rules

- **Pagination**: `limit` (default 10) and `offset` (default 0). Iterate until a page returns fewer items than `limit`. Results live under `data.<collection>`.
- **Rate limits**: 100/min and 10,000/day on Expert, 200/min and 20,000/day on Enterprise, counted **per account, not per key**. Read `x-ratelimit-minute-remaining` and `x-ratelimit-day-remaining` on every response and back off exponentially on `429`. Bulk-create in batches rather than one call per employee.
- **Errors**: `422` returns `{"detail":[{"loc":[...],"msg":"...","type":"..."}]}`. Domain errors (400/403/404/409) return `{"error":"CODE: message","path":"...","request_id":"..."}` — log `request_id` before escalating. There is no `application/problem+json`.
- **Forward compatibility**: parse responses leniently; Connecteam adds response fields without a version bump.
- **Deprovisioning** is the mirror flow: `archive_users_users_v1_users_delete` (archive, reversible) before `delete_user_users_v1_users__userId__delete` (permanent).

Cross-references: `conventions/connecteam-conventions.yml`, `errors/connecteam-problem-types.yml`, `scopes/connecteam-scopes.yml`, `plans/connecteam-plans.yml`.
