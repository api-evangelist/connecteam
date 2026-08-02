---
name: Clock employees in and out and reconcile timesheets
description: Drive the Connecteam time clock — clock in/out, manual breaks, create and correct time activities, pull timesheet totals, and lock days for payroll.
api: openapi/connecteam-openapi-original.json
generated: '2026-08-01'
method: generated
source: openapi/connecteam-openapi-original.json + https://developer.connecteam.com/docs/time-clock-overview
operations:
  - get_time_clocks_time_clock_v1_time_clocks_get
  - clock_user_in_time_clock_v1_time_clocks__timeClockId__clock_in_post
  - clock_user_out_time_clock_v1_time_clocks__timeClockId__clock_out_post
  - get_manual_breaks_time_clock_v1_time_clocks__timeClockId__manual_breaks_get
  - clock_in_manual_break_time_clock_v1_time_clocks__timeClockId__manual_breaks__manualBreakId__clock_in_post
  - clock_out_manual_break_time_clock_v1_time_clocks__timeClockId__manual_breaks_clock_out_post
  - get_time_activities_time_clock_v1_time_clocks__timeClockId__time_activities_get
  - create_time_activities_time_clock_v1_time_clocks__timeClockId__time_activities_post
  - delete_time_activity_time_clock_v1_time_clocks__timeClockId__time_activities__timeActivityId__delete
  - get_timesheet_total_hours_time_clock_v1_time_clocks__timeClockId__timesheet_get
  - update_user_lock_days_time_clock_v1_time_clocks__timeClockId__users__userId__lock_days_put
scopes:
  - time_clock.read
  - time_clock.write
  - time_clock.delete
---

# Clock employees in and out and reconcile timesheets

Base URL `https://api.connecteam.com`. Requires the **Operations** hub on Expert or above.

## Steps

1. **Resolve the time clock.** `get_time_clocks_time_clock_v1_time_clocks_get` (`GET /time-clock/v1/time-clocks`) — every downstream call is nested under `{timeClockId}`.
2. **Clock in / clock out in real time.** `clock_user_in_time_clock_v1_time_clocks__timeClockId__clock_in_post` and `clock_user_out_time_clock_v1_time_clocks__timeClockId__clock_out_post`. Both are real-time operations tied to the user's current state — clocking in a user who is already clocked in is a domain error, not a no-op. Read the current state from `get_time_activities_time_clock_v1_time_clocks__timeClockId__time_activities_get` before acting.
3. **Manual breaks.** List with `get_manual_breaks_time_clock_v1_time_clocks__timeClockId__manual_breaks_get`, start with `clock_in_manual_break_time_clock_v1_time_clocks__timeClockId__manual_breaks__manualBreakId__clock_in_post`, end with `clock_out_manual_break_time_clock_v1_time_clocks__timeClockId__manual_breaks_clock_out_post`.
4. **Backfill or correct history.** `create_time_activities_time_clock_v1_time_clocks__timeClockId__time_activities_post` writes completed activities with explicit start/end times. Remove a bad one with `delete_time_activity_time_clock_v1_time_clocks__timeClockId__time_activities__timeActivityId__delete` — a missing or already-deleted activity returns `404 TIME_ACTIVITY_NOT_FOUND`.
5. **Attach geofence context.** `get_geofences_time_clock_v1_time_clocks__timeClockId__geofences_get` / `create_geofences_time_clock_v1_time_clocks__timeClockId__geofences_post` when clock events must be constrained to a site.
6. **Pull totals for payroll.** `get_timesheet_total_hours_time_clock_v1_time_clocks__timeClockId__timesheet_get` over the pay period window.
7. **Lock the period.** `update_user_lock_days_time_clock_v1_time_clocks__timeClockId__users__userId__lock_days_put` with `isLocked: true`. This is the **one genuinely idempotent operation in the API**: dates already in the requested state are no-ops and the response reflects the final state, so it is safe to retry.
8. **Location audit (optional).** `generate_breadcrumbs_report_time_clock_breadcrumbs_v1_report_post` returns a request id; poll `get_report_status_time_clock_breadcrumbs_v1_report__fileId__get` until status is `completed`, then stream it with `download_breadcrumbs_report_time_clock_breadcrumbs_v1_report__fileId__download_get`.

## Rules

- **Unlocking is guarded.** `isLocked: false` on any date inside an approved payroll period rejects the **entire** request with `409 DAYS_IN_APPROVED_PERIOD` and unlocks nothing. Reopen the approved period from the dashboard first. `isLocked: true` on an approved-period day is allowed and is a no-op.
- **Lock days must be enabled.** If Timesheet Approval (Lock Days) is off for the time clock, the call returns `403 LOCK_DAYS_DISABLED`.
- **Pay rates collide with locks.** Deleting a pay rate whose effective date touches approved or locked days fails with `HAS_LOCKED_DAYS`.
- **Retries create duplicates.** `create_time_activities...` is a POST with no idempotency key. On an ambiguous failure, re-read with `get_time_activities...` for the same user and window before resending.
- **Rate limits** are per account: 100/min on Expert, 200/min on Enterprise. Batch a shift's worth of activities into one call rather than one call per employee.
- **Watch the events instead of polling.** 17 of the 41 declared webhooks are time-activity events (clock in, clock out, auto clock out, admin add/edit/delete, and the approved/declined request variants). Subscribe with `create_webhook_settings_v1_webhooks_post` using `featureType: "time_activity"` and the `timeClockId` as `objectId`.

Cross-references: `asyncapi/connecteam-events-webhooks.yml`, `errors/connecteam-problem-types.yml`, `conventions/connecteam-conventions.yml`.
