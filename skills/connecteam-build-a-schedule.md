---
name: Build and publish a shift schedule
description: Create, read, update and delete shifts on a Connecteam scheduler, respect unavailability, and run auto-assign — including the v1 vs v2 shift-model split.
api: openapi/connecteam-openapi-original.json
generated: '2026-08-01'
method: generated
source: openapi/connecteam-openapi-original.json + https://developer.connecteam.com/docs/scheduler-overview
operations:
  - get_schedulers_scheduler_v1_schedulers_get
  - get_shifts_scheduler_v1_schedulers__schedulerId__shifts_get
  - create_shifts_scheduler_v1_schedulers__schedulerId__shifts_post
  - get_shift_by_id_scheduler_v1_schedulers__schedulerId__shifts__shiftId__get
  - delete_shifts_by_ids_scheduler_v1_schedulers__schedulerId__shifts_delete
  - get_unavailabilities_scheduler_v1_schedulers__schedulerId__unavailabilities_get
  - create_autofill_request_scheduler_v2_schedulers__schedulerId__shifts_auto_assign_post
  - get_autofill_status_scheduler_v2_schedulers__schedulerId__shifts_auto_assign__autoAssignRequestId__get
  - get_shift_custom_fields_scheduler_v1_schedulers__schedulerId__custom_fields_get
  - get_shift_layers_scheduler_v1_schedulers__schedulerId__shift_layers_get
scopes:
  - schedule.read
  - schedule.write
  - schedule.delete
---

# Build and publish a shift schedule

Base URL `https://api.connecteam.com`. Requires the **Operations** hub on Expert or above.

## Choose your shift model first

Connecteam runs two shift APIs side by side and they are not interchangeable:

- **v1** (`/scheduler/v1/...`) — one record per *user assignment*. A three-person shift is three shifts with three ids.
- **v2** (`/scheduler/v2/...`) — one *base shift* carrying a list of assigned user ids.

Pick one and stay on it for a given integration; ids from one version are not valid in the other. The migration guide is at https://developer.connecteam.com/docs/scheduler-shifts-vision-migration.

## Steps

1. **List schedulers.** `get_schedulers_scheduler_v1_schedulers_get` (`GET /scheduler/v1/schedulers`) — everything nests under `{schedulerId}`.
2. **Read the shift shape.** `get_shift_custom_fields_scheduler_v1_schedulers__schedulerId__custom_fields_get` and `get_shift_layers_scheduler_v1_schedulers__schedulerId__shift_layers_get` (plus `get_shift_layer_values_scheduler_v1_schedulers__schedulerId__shift_layers__layerId__values_get`) so you post valid custom-field and layer values.
3. **Check who cannot work.** `get_unavailabilities_scheduler_v1_schedulers__schedulerId__unavailabilities_get` for scheduler-level unavailability and `get_unavailabilities_scheduler_v1_schedulers_user_unavailability_get` (v2: `..._scheduler_v2_...`) for per-user unavailability. Cross-check approved time off with `list_time_off_requests_time_off_v1_requests_get`.
4. **Create the shifts.** `create_shifts_scheduler_v1_schedulers__schedulerId__shifts_post` (or the v2 sibling). This accepts a batch — post a week at a time rather than one call per shift.
5. **Read back.** `get_shifts_scheduler_v1_schedulers__schedulerId__shifts_get` over the date window, or `get_shift_by_id_scheduler_v1_schedulers__schedulerId__shifts__shiftId__get` for one.
6. **Amend.** `update_shifts_scheduler_v1_schedulers__schedulerId__shifts_put`. On the v2 model, targeted base/group edits require `assignedUserIds` when `isEditForAllUsers` is explicitly `false` — omitting it returns `400`.
7. **Remove.** `delete_shift_by_id_scheduler_v1_schedulers__schedulerId__shifts__shiftId__delete` for one, `delete_shifts_by_ids_scheduler_v1_schedulers__schedulerId__shifts_delete` for a batch.
8. **Let Connecteam fill the gaps.** `create_autofill_request_scheduler_v2_schedulers__schedulerId__shifts_auto_assign_post` submits shift ids for auto-assignment; all ids must fall in the same work week. It is **asynchronous** — it returns a request id and processing takes minutes. Poll `get_autofill_status_scheduler_v2_schedulers__schedulerId__shifts_auto_assign__autoAssignRequestId__get`, which splits the outcome into scheduled and unscheduled shifts. Auto-assign already honours user work preferences, unavailability and approved time off.

## Rules

- **Do not retry blind.** `create_shifts...` is a non-idempotent POST. If a create times out, re-read the window with `get_shifts...` before resending or you will double-book.
- **Webhook parity matters.** The shift webhooks (`Shifts created`, `Shifts updated`, `Shifts deleted`) default to **V1** semantics — one event per user assignment. V2 aggregates assignments into one event and turns "add a user to an existing shift" into a `shift.updated`. V2 webhook behaviour must be enabled per account by contacting Connecteam; do not assume it. See https://developer.connecteam.com/docs/shift-webhook-v1-vs-v2.
- **Pagination**: `limit` / `offset`, plus `startDate` / `endDate` window filters on the list endpoints.
- **Rate limits**: per account, 100/min on Expert. A full-week publish should be a handful of batched calls, not hundreds.
- **Errors**: `422` for schema violations, `400` for shift-model rule violations; both are `application/json`, neither is RFC 9457.

Cross-references: `conventions/connecteam-conventions.yml`, `lifecycle/connecteam-lifecycle.yml`, `asyncapi/connecteam-events-webhooks.yml`.
