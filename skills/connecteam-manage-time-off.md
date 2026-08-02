---
name: Manage time-off policies, balances and requests
description: Read Connecteam time-off policy types, assign them to employees, adjust balances, and create or approve time-off requests.
api: openapi/connecteam-openapi-original.json
generated: '2026-08-01'
method: generated
source: openapi/connecteam-openapi-original.json + https://developer.connecteam.com/docs/time-off-overview
operations:
  - get_policy_groups_time_off_v1_policy_types_get
  - assign_user_to_policy_time_off_v1_time_off_policies__timeOffPolicyId__assignments_put
  - get_balances_time_off_v1_policy_types__policyTypeId__balances_get
  - put_user_balance_time_off_v1_policy_types__policyTypeId__balances__userId__put
  - list_time_off_requests_time_off_v1_requests_get
  - post_time_off_request_time_off_v1_requests_post
  - put_time_off_request_time_off_v1_requests__requestId__put
scopes:
  - time_off.read
  - time_off.write
---

# Manage time-off policies, balances and requests

Base URL `https://api.connecteam.com`. Requires the **HR & Skills** hub on Expert or above.

## Steps

1. **List policy types.** `get_policy_groups_time_off_v1_policy_types_get` (`GET /time-off/v1/policy-types`). Each policy type carries its unit (hours or days) and, since the 2026-07-13 release, its `accrualType` and `policyId` — read the unit before you compute anything, because balances and request durations are expressed in the policy's own units.
2. **Assign a policy to an employee.** `assign_user_to_policy_time_off_v1_time_off_policies__timeOffPolicyId__assignments_put`.
3. **Read balances.** `get_balances_time_off_v1_policy_types__policyTypeId__balances_get` for everyone on a policy type.
4. **Adjust a balance.** `put_user_balance_time_off_v1_policy_types__policyTypeId__balances__userId__put`. Use this for opening balances on migration and for manual corrections; accrual-based policies otherwise manage themselves.
5. **List requests.** `list_time_off_requests_time_off_v1_requests_get` (`GET /time-off/v1/requests`) returns requests whose date range **overlaps** the requested window, optionally filtered by employees and statuses. It **defaults to approved status when no status filter is given** — always pass the status filter explicitly if you want pending or declined requests too. Approved requests include `duration` (the amount deducted from balance, in policy units); it is omitted for every other status.
6. **Create a request.** `post_time_off_request_time_off_v1_requests_post`.
7. **Update or decide a request.** `put_time_off_request_time_off_v1_requests__requestId__put`.

## Rules

- **The default filter is a trap.** A sync that calls `list_time_off_requests...` with no status filter silently sees only approved requests and will never notice pending ones. Pass statuses explicitly.
- **Overlap, not containment.** The window filter matches requests that overlap the range, so a request starting before your window will appear. De-duplicate on request id across runs.
- **`duration` is conditional.** Do not assume the field exists; branch on status.
- **Not idempotent.** `post_time_off_request...` has no idempotency key. On an ambiguous failure, re-list the employee's requests for that window before resending.
- **Schedule interaction.** Approved time off is honoured by the scheduler's auto-assign (`create_autofill_request_scheduler_v2_schedulers__schedulerId__shifts_auto_assign_post`), so approve before you auto-fill a week rather than after.
- **Errors**: `422` with `{"detail":[...]}` for schema violations; domain errors return `{"error":"CODE: message","path":"...","request_id":"..."}`.
- **Pagination**: `limit` / `offset`; results under `data.<collection>`.

Cross-references: `conventions/connecteam-conventions.yml`, `changelog/connecteam-changelog.yml`, `plans/connecteam-plans.yml`.
