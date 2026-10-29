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

Connecteam is a mobile-first workforce management platform for deskless and non-desk teams, bundling time clock and GPS timesheets, job scheduling, task boards, digital forms and checklists, chat and company communication, HR onboarding, time off, pay rates and sales data into three purchasable hubs (Operations, Communications, HR & Skills). Its public REST API at api.connecteam.com is described by an OpenAPI 3.1 contract covering 145 operations across 98 paths, authenticated either with a company X-API-KEY header or OAuth 2.0 client-credentials tokens scoped across 61 named permissions, and it declares 41 webhook events for time activity, shifts, users, tasks, forms and chat. API access is gated to the Expert plan and above, with per-plan rate limits surfaced in x-ratelimit-* response headers.

**Areas:** Company · Workforce Management · Human Resources · Time Tracking · Scheduling · Employee Communication · Task Management · Forms · Deskless · Software-as-a-Service

## Connecteam on APIs.io

Everything profiled for Connecteam is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/connecteam/](https://apis.io/providers/connecteam/)** — or go straight to one of the APIs or properties below.

### APIs (69)

- [Connecteam Account API](https://apis.io/apis/connecteam/connecteam-account-api/) — The Account API from Connecteam — 1 operation(s) for account.
- [Connecteam Assets:v1:Asset API](https://apis.io/apis/connecteam/connecteam-assets-v1-asset-api/) — The Assets:v1:Asset API from Connecteam — 1 operation(s) for assets:v1:asset.
- [Connecteam Attachments:v1:Files API](https://apis.io/apis/connecteam/connecteam-attachments-v1-files-api/) — The Attachments:v1:Files API from Connecteam — 4 operation(s) for attachments:v1:files.
- [Connecteam Breadcrumbs:Breadcrumbs API](https://apis.io/apis/connecteam/connecteam-breadcrumbs-breadcrumbs-api/) — The Breadcrumbs:Breadcrumbs API from Connecteam — 3 operation(s) for breadcrumbs:breadcrumbs.
- [Connecteam Chat:v1:Conversations API](https://apis.io/apis/connecteam/connecteam-chat-v1-conversations-api/) — The Chat:v1:Conversations API from Connecteam — 3 operation(s) for chat:v1:conversations.
- [Connecteam Company Policies:v1:PayRuleAssignment API](https://apis.io/apis/connecteam/connecteam-company-policies-v1-payruleassignment-api/) — The Company Policies:v1:PayRuleAssignment API from Connecteam — 1 operation(s) for company policies:v1:payruleassignment.
- [Connecteam Company Policies:v1:PayRulePolicies API](https://apis.io/apis/connecteam/connecteam-company-policies-v1-payrulepolicies-api/) — The Company Policies:v1:PayRulePolicies API from Connecteam — 1 operation(s) for company policies:v1:payrulepolicies.
- [Connecteam API Documentation API](https://apis.io/apis/connecteam/connecteam-connecteam-api-documentation-api/) — The Connecteam API Documentation API from Connecteam — 0 operation(s) for connecteam api documentation.
- [Connecteam Daily Note:v1:Daily Note API](https://apis.io/apis/connecteam/connecteam-dailynote-v1-dailynote-api/) — The DailyNote:v1:DailyNote API from Connecteam — 1 operation(s) for dailynote:v1:dailynote.
- [Connecteam Daily Note:v1:Daily Notes API](https://apis.io/apis/connecteam/connecteam-dailynote-v1-dailynotes-api/) — The DailyNote:v1:DailyNotes API from Connecteam — 1 operation(s) for dailynote:v1:dailynotes.
- [Connecteam Forms:v1:Form Submissions API](https://apis.io/apis/connecteam/connecteam-forms-v1-form-submissions-api/) — The Forms:v1:Form Submissions API from Connecteam — 2 operation(s) for forms:v1:form submissions.
- [Connecteam Forms:v1:Forms API](https://apis.io/apis/connecteam/connecteam-forms-v1-forms-api/) — The Forms:v1:Forms API from Connecteam — 2 operation(s) for forms:v1:forms.
- [Connecteam Forms:v1:Questions API](https://apis.io/apis/connecteam/connecteam-forms-v1-questions-api/) — The Forms:v1:Questions API from Connecteam — 2 operation(s) for forms:v1:questions.
- [Connecteam Jobs:v1:Custom Fields API](https://apis.io/apis/connecteam/connecteam-jobs-v1-custom-fields-api/) — The Jobs:v1:Custom Fields API from Connecteam — 1 operation(s) for jobs:v1:custom fields.
- [Connecteam Jobs:v1:Job API](https://apis.io/apis/connecteam/connecteam-jobs-v1-job-api/) — The Jobs:v1:Job API from Connecteam — 1 operation(s) for jobs:v1:job.
- [Connecteam Jobs:v1:Jobs API](https://apis.io/apis/connecteam/connecteam-jobs-v1-jobs-api/) — The Jobs:v1:Jobs API from Connecteam — 1 operation(s) for jobs:v1:jobs.
- [Connecteam Onboarding:v1:Onboarding:Assignments API](https://apis.io/apis/connecteam/connecteam-onboarding-v1-onboarding-assignments-api/) — The Onboarding:v1:Onboarding:Assignments API from Connecteam — 1 operation(s) for onboarding:v1:onboarding:assignments.
- [Connecteam Onboarding:v1:Onboarding:Packs API](https://apis.io/apis/connecteam/connecteam-onboarding-v1-onboarding-packs-api/) — The Onboarding:v1:Onboarding:Packs API from Connecteam — 1 operation(s) for onboarding:v1:onboarding:packs.
- [Connecteam Pay Rates:v1:Pay Rates:v1:PayRates API](https://apis.io/apis/connecteam/connecteam-pay-rates-v1-pay-rates-v1-payrates-api/) — The Pay Rates:v1:Pay Rates:v1:PayRates API from Connecteam — 2 operation(s) for pay rates:v1:pay rates:v1:payrates.
- [Connecteam Publishers:v1:Publishers API](https://apis.io/apis/connecteam/connecteam-publishers-v1-publishers-api/) — The Publishers:v1:Publishers API from Connecteam — 1 operation(s) for publishers:v1:publishers.
- [Connecteam Sales:Sales V1:Sales Daily API](https://apis.io/apis/connecteam/connecteam-sales-sales-v1-sales-daily-api/) — The Sales:Sales V1:Sales Daily API from Connecteam — 1 operation(s) for sales:sales v1:sales daily.
- [Connecteam Sales:Sales V1:Sales Locations API](https://apis.io/apis/connecteam/connecteam-sales-sales-v1-sales-locations-api/) — The Sales:Sales V1:Sales Locations API from Connecteam — 1 operation(s) for sales:sales v1:sales locations.
- [Connecteam Sales:Sales V1:Sales Locations:Sales Daily API](https://apis.io/apis/connecteam/connecteam-sales-sales-v1-sales-locations-sales-daily-api/) — The Sales:Sales V1:Sales Locations:Sales Daily API from Connecteam — 1 operation(s) for sales:sales v1:sales locations:sales daily.
- [Connecteam Sales:Sales V1:Sales Transactions API](https://apis.io/apis/connecteam/connecteam-sales-sales-v1-sales-transactions-api/) — The Sales:Sales V1:Sales Transactions API from Connecteam — 2 operation(s) for sales:sales v1:sales transactions.
- [Connecteam Schedule:v1:Schedulers API](https://apis.io/apis/connecteam/connecteam-schedule-v1-schedulers-api/) — The Schedule:v1:Schedulers API from Connecteam — 1 operation(s) for schedule:v1:schedulers.
- [Connecteam Schedule:v1:Schedulers:Schedule:Schedule Unavailabilities API](https://apis.io/apis/connecteam/connecteam-schedule-v1-schedulers-schedule-schedule-unavailabilities-api/) — The Schedule:v1:Schedulers:Schedule:Schedule Unavailabilities API from Connecteam — 1 operation(s) for schedule:v1:schedulers:schedule:schedule…
- [Connecteam Schedule:v1:Schedulers:Schedule:Schedule Unavailability API](https://apis.io/apis/connecteam/connecteam-schedule-v1-schedulers-schedule-schedule-unavailability-api/) — The Schedule:v1:Schedulers:Schedule:Schedule Unavailability API from Connecteam — 2 operation(s) for schedule:v1:schedulers:schedule:schedule unavailability.
- [Connecteam Schedule:v1:Schedulers:Schedule:Shift Auto Assign API](https://apis.io/apis/connecteam/connecteam-schedule-v1-schedulers-schedule-shift-auto-assign-api/) — The Schedule:v1:Schedulers:Schedule:Shift Auto Assign API from Connecteam — 2 operation(s) for schedule:v1:schedulers:schedule:shift auto assign.
- [Connecteam Schedule:v1:Schedulers:Schedule:Shift Custom Fields API](https://apis.io/apis/connecteam/connecteam-schedule-v1-schedulers-schedule-shift-custom-fields-api/) — The Schedule:v1:Schedulers:Schedule:Shift Custom Fields API from Connecteam — 1 operation(s) for schedule:v1:schedulers:schedule:shift custom fields.
- [Connecteam Schedule:v1:Schedulers:Schedule:Shift layers API](https://apis.io/apis/connecteam/connecteam-schedule-v1-schedulers-schedule-shift-layers-api/) — The Schedule:v1:Schedulers:Schedule:Shift layers API from Connecteam — 2 operation(s) for schedule:v1:schedulers:schedule:shift layers.
- [Connecteam Schedule:v1:Schedulers:Schedule:Shifts:Shifts API](https://apis.io/apis/connecteam/connecteam-schedule-v1-schedulers-schedule-shifts-shifts-api/) — The Schedule:v1:Schedulers:Schedule:Shifts:Shifts API from Connecteam — 2 operation(s) for schedule:v1:schedulers:schedule:shifts:shifts.
- [Connecteam Schedule:v1:Schedulers:Unavailabilities API](https://apis.io/apis/connecteam/connecteam-schedule-v1-schedulers-unavailabilities-api/) — The Schedule:v1:Schedulers:Unavailabilities API from Connecteam — 1 operation(s) for schedule:v1:schedulers:unavailabilities.
- [Connecteam Schedule:v2:Schedulers:Schedule:Shift Auto Assign (V2):Shift Auto Assign API](https://apis.io/apis/connecteam/connecteam-schedule-v2-schedulers-schedule-shift-auto-assign-v2-shift-auto-assign-api/) — The Schedule:v2:Schedulers:Schedule:Shift Auto Assign (V2):Shift Auto Assign API from Connecteam — 2 operation(s) for schedule:v2:schedulers:schedule:shift…
- [Connecteam Schedule:v2:Schedulers:Schedule:Shifts (V2):Shifts API](https://apis.io/apis/connecteam/connecteam-schedule-v2-schedulers-schedule-shifts-v2-shifts-api/) — The Schedule:v2:Schedulers:Schedule:Shifts (V2):Shifts API from Connecteam — 2 operation(s) for schedule:v2:schedulers:schedule:shifts (v2):shifts.
- [Connecteam Schedule:v2:Schedulers:Unavailabilities (V2):Unavailabilities API](https://apis.io/apis/connecteam/connecteam-schedule-v2-schedulers-unavailabilities-v2-unavailabilities-api/) — The Schedule:v2:Schedulers:Unavailabilities (V2):Unavailabilities API from Connecteam — 1 operation(s) for schedule:v2:schedulers:unavailabilities…
- [Connecteam Settings:v1:Webhook API](https://apis.io/apis/connecteam/connecteam-settings-v1-webhook-api/) — The Settings:v1:Webhook API from Connecteam — 2 operation(s) for settings:v1:webhook.
- [Connecteam Tasks:v1:Sub Tasks:Tasks:Task Boards API](https://apis.io/apis/connecteam/connecteam-tasks-v1-subtasks-tasks-taskboards-api/) — The Tasks:v1:SubTasks:Tasks:TaskBoards API from Connecteam — 2 operation(s) for tasks:v1:subtasks:tasks:taskboards.
- [Connecteam Tasks:v1:Task Boards API](https://apis.io/apis/connecteam/connecteam-tasks-v1-taskboards-api/) — The Tasks:v1:TaskBoards API from Connecteam — 1 operation(s) for tasks:v1:taskboards.
- [Connecteam Tasks:v1:Task Labels API](https://apis.io/apis/connecteam/connecteam-tasks-v1-tasklabels-api/) — The Tasks:v1:TaskLabels API from Connecteam — 1 operation(s) for tasks:v1:tasklabels.
- [Connecteam Tasks:v1:Tasks:Tasks Boards API](https://apis.io/apis/connecteam/connecteam-tasks-v1-tasks-tasksboards-api/) — The Tasks:v1:Tasks:TasksBoards API from Connecteam — 2 operation(s) for tasks:v1:tasks:tasksboards.
- [Connecteam Time Clock:v1:TimeClocks API](https://apis.io/apis/connecteam/connecteam-time-clock-v1-timeclocks-api/) — The Time Clock:v1:TimeClocks API from Connecteam — 1 operation(s) for time clock:v1:timeclocks.
- [Connecteam Time Clock:v1:TimeClocks:TimeClock:ClockIn API](https://apis.io/apis/connecteam/connecteam-time-clock-v1-timeclocks-timeclock-clockin-api/) — The Time Clock:v1:TimeClocks:TimeClock:ClockIn API from Connecteam — 1 operation(s) for time clock:v1:timeclocks:timeclock:clockin.
- [Connecteam Time Clock:v1:TimeClocks:TimeClock:ClockOut API](https://apis.io/apis/connecteam/connecteam-time-clock-v1-timeclocks-timeclock-clockout-api/) — The Time Clock:v1:TimeClocks:TimeClock:ClockOut API from Connecteam — 1 operation(s) for time clock:v1:timeclocks:timeclock:clockout.
- [Connecteam Time Clock:v1:TimeClocks:TimeClock:GeoFences API](https://apis.io/apis/connecteam/connecteam-time-clock-v1-timeclocks-timeclock-geofences-api/) — The Time Clock:v1:TimeClocks:TimeClock:GeoFences API from Connecteam — 2 operation(s) for time clock:v1:timeclocks:timeclock:geofences.
- [Connecteam Time Clock:v1:TimeClocks:TimeClock:Get timesheet totals API](https://apis.io/apis/connecteam/connecteam-time-clock-v1-timeclocks-timeclock-get-timesheet-totals-api/) — The Time Clock:v1:TimeClocks:TimeClock:Get timesheet totals API from Connecteam — 1 operation(s) for time clock:v1:timeclocks:timeclock:get timesheet totals.
- [Connecteam Time Clock:v1:TimeClocks:TimeClock:LockDays API](https://apis.io/apis/connecteam/connecteam-time-clock-v1-timeclocks-timeclock-lockdays-api/) — The Time Clock:v1:TimeClocks:TimeClock:LockDays API from Connecteam — 1 operation(s) for time clock:v1:timeclocks:timeclock:lockdays.
- [Connecteam Time Clock:v1:TimeClocks:TimeClock:ManualBreaks API](https://apis.io/apis/connecteam/connecteam-time-clock-v1-timeclocks-timeclock-manualbreaks-api/) — The Time Clock:v1:TimeClocks:TimeClock:ManualBreaks API from Connecteam — 1 operation(s) for time clock:v1:timeclocks:timeclock:manualbreaks.
- [Connecteam Time Clock:v1:TimeClocks:TimeClock:ManualBreaks:ManualBreakClockIn API](https://apis.io/apis/connecteam/connecteam-time-clock-v1-timeclocks-timeclock-manualbreaks-manualbreakclockin-api/) — The Time Clock:v1:TimeClocks:TimeClock:ManualBreaks:ManualBreakClockIn API from Connecteam — 1 operation(s) for time…
- [Connecteam Time Clock:v1:TimeClocks:TimeClock:ManualBreaks:ManualBreakClockOut API](https://apis.io/apis/connecteam/connecteam-time-clock-v1-timeclocks-timeclock-manualbreaks-manualbreakclockout-api/) — The Time Clock:v1:TimeClocks:TimeClock:ManualBreaks:ManualBreakClockOut API from Connecteam — 1 operation(s) for time…
- [Connecteam Time Clock:v1:TimeClocks:TimeClock:ShiftAttachments API](https://apis.io/apis/connecteam/connecteam-time-clock-v1-timeclocks-timeclock-shiftattachments-api/) — The Time Clock:v1:TimeClocks:TimeClock:ShiftAttachments API from Connecteam — 1 operation(s) for time clock:v1:timeclocks:timeclock:shiftattachments.
- [Connecteam Time Clock:v1:TimeClocks:TimeClock:TimeActivities API](https://apis.io/apis/connecteam/connecteam-time-clock-v1-timeclocks-timeclock-timeactivities-api/) — The Time Clock:v1:TimeClocks:TimeClock:TimeActivities API from Connecteam — 2 operation(s) for time clock:v1:timeclocks:timeclock:timeactivities.
- [Connecteam Time Off:v1:Balances API](https://apis.io/apis/connecteam/connecteam-time-off-v1-balances-api/) — The Time Off:v1:Balances API from Connecteam — 2 operation(s) for time off:v1:balances.
- [Connecteam Time Off:v1:PolicyAssignment API](https://apis.io/apis/connecteam/connecteam-time-off-v1-policyassignment-api/) — The Time Off:v1:PolicyAssignment API from Connecteam — 1 operation(s) for time off:v1:policyassignment.
- [Connecteam Time Off:v1:PolicyTypes API](https://apis.io/apis/connecteam/connecteam-time-off-v1-policytypes-api/) — The Time Off:v1:PolicyTypes API from Connecteam — 1 operation(s) for time off:v1:policytypes.
- [Connecteam Time Off:v1:TimeOffRequests API](https://apis.io/apis/connecteam/connecteam-time-off-v1-timeoffrequests-api/) — The Time Off:v1:TimeOffRequests API from Connecteam — 2 operation(s) for time off:v1:timeoffrequests.
- [Connecteam Users:v1:Admins API](https://apis.io/apis/connecteam/connecteam-users-v1-admins-api/) — The Users:v1:Admins API from Connecteam — 1 operation(s) for users:v1:admins.
- [Connecteam Users:v1:Assignments API](https://apis.io/apis/connecteam/connecteam-users-v1-assignments-api/) — The Users:v1:Assignments API from Connecteam — 1 operation(s) for users:v1:assignments.
- [Connecteam Users:v1:Custom Field Categories API](https://apis.io/apis/connecteam/connecteam-users-v1-custom-field-categories-api/) — The Users:v1:Custom Field Categories API from Connecteam — 1 operation(s) for users:v1:custom field categories.
- [Connecteam Users:v1:Custom Fields API](https://apis.io/apis/connecteam/connecteam-users-v1-custom-fields-api/) — The Users:v1:Custom Fields API from Connecteam — 1 operation(s) for users:v1:custom fields.
- [Connecteam Users:v1:Custom Fields:Custom Field options API](https://apis.io/apis/connecteam/connecteam-users-v1-custom-fields-custom-field-options-api/) — The Users:v1:Custom Fields:Custom Field options API from Connecteam — 2 operation(s) for users:v1:custom fields:custom field options.
- [Connecteam Users:v1:Notes API](https://apis.io/apis/connecteam/connecteam-users-v1-notes-api/) — The Users:v1:Notes API from Connecteam — 1 operation(s) for users:v1:notes.
- [Connecteam Users:v1:Payslips API](https://apis.io/apis/connecteam/connecteam-users-v1-payslips-api/) — The Users:v1:Payslips API from Connecteam — 1 operation(s) for users:v1:payslips.
- [Connecteam Users:v1:Pending Request Users API](https://apis.io/apis/connecteam/connecteam-users-v1-pending-request-users-api/) — The Users:v1:Pending Request Users API from Connecteam — 3 operation(s) for users:v1:pending request users.
- [Connecteam Users:v1:Performance API](https://apis.io/apis/connecteam/connecteam-users-v1-performance-api/) — The Users:v1:Performance API from Connecteam — 1 operation(s) for users:v1:performance.
- [Connecteam Users:v1:Performance Indicators API](https://apis.io/apis/connecteam/connecteam-users-v1-performance-indicators-api/) — The Users:v1:Performance Indicators API from Connecteam — 1 operation(s) for users:v1:performance indicators.
- [Connecteam Users:v1:Smart Group Segments API](https://apis.io/apis/connecteam/connecteam-users-v1-smart-group-segments-api/) — The Users:v1:Smart Group Segments API from Connecteam — 1 operation(s) for users:v1:smart group segments.
- [Connecteam Users:v1:Smart Groups API](https://apis.io/apis/connecteam/connecteam-users-v1-smart-groups-api/) — The Users:v1:Smart Groups API from Connecteam — 2 operation(s) for users:v1:smart groups.
- [Connecteam Users:v1:Users API](https://apis.io/apis/connecteam/connecteam-users-v1-users-api/) — The Users:v1:Users API from Connecteam — 2 operation(s) for users:v1:users.
- [Connecteam O Auth API](https://apis.io/apis/connecteam/connecteam-oauth-api/) — The OAuth API from Connecteam — 1 operation(s) for oauth.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Connecteam Events Webhooks](https://apis.io/asyncapis/connecteam/connecteam-events-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [connecteam](https://apis.io/servers/connecteam/connecteam/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Connecteam Agentic Access](https://apis.io/agentic-access/connecteam/connecteam-agentic-access/)

#### Collections (1)

Postman and Open Collection request collections.

- [Connecteam API documentation](https://apis.io/collections/connecteam/open-connecteam-openapi-original/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Connecteam Api Overlay](https://apis.io/overlays/connecteam/connecteam-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Connecteam Authentication](https://apis.io/security/connecteam/connecteam-authentication/)
- [Connecteam Domain Security](https://apis.io/security/connecteam/connecteam-domain-security/)
- [Connecteam Trust Center](https://apis.io/security/connecteam/connecteam-trust-center/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Connecteam Scopes](https://apis.io/scopes/connecteam/connecteam-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Connecteam Plans](https://apis.io/plans/connecteam/connecteam-plans/)

#### Rate limits (1)

Published request limits.

- [Connecteam Rate Limits](https://apis.io/rate-limits/connecteam/connecteam-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://connecteam.com/)
- [Documentation](https://developer.connecteam.com/docs/introduction-1)
- [Getting started](https://developer.connecteam.com/docs/introduction-1)
- [API reference](https://developer.connecteam.com/reference/)
- [Pricing](https://connecteam.com/pricing/)
- [Sign up](https://connecteam.com/employee-app-360-funnel/)
- [Support](https://help.connecteam.com/en/)
- [Changelog](https://developer.connecteam.com/changelog)
- [Blog](https://connecteam.com/blog/)
- [Compliance](https://connecteam.com/trust-center/)
- [Terms of service](https://connecteam.com/terms-conditions/)
- [Privacy policy](https://connecteam.com/privacy/)
- [GitHub](https://github.com/Connecteam)
- [Status](https://connecteam.statuspage.io/)

## API Evangelist rating

**Kin Score 62.9** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 61.6 |
| Contract governance | 4.5 |
| Operational transparency | 73.7 |
| Developer ergonomics | 39.9 |
| Access clarity | 92.1 |

**Agent readiness 44.5** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | verified |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | derived (partial credit) |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 39.2** — Employment & Payroll

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/connecteam/](https://apis.io/providers/connecteam/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Connecteam: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/connecteam/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
