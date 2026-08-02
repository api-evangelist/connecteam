---
name: Collect and export digital form submissions
description: Enumerate Connecteam forms, read their question and dropdown structure, and pull submissions plus their file attachments on a schedule or by event.
api: openapi/connecteam-openapi-original.json
generated: '2026-08-01'
method: generated
source: openapi/connecteam-openapi-original.json + https://developer.connecteam.com/docs/forms-overview
operations:
  - get_forms_forms_v1_forms_get
  - get_form_forms_v1_forms__formId__get
  - get_dropdown_question_options_forms_v1_forms__formId__questions__questionId__get
  - get_form_submissions_forms_v1_forms__formId__form_submissions_get
  - get_form_submission_forms_v1_forms__formId__form_submissions__formSubmissionId__get
  - get_file_url_attachments_v1_files__fileId__get
  - create_webhook_settings_v1_webhooks_post
scopes:
  - forms.read
  - attachments.read
  - settings.write
---

# Collect and export digital form submissions

Base URL `https://api.connecteam.com`. Requires the **Operations** hub on Expert or above.

## Steps

1. **List forms.** `get_forms_forms_v1_forms_get` (`GET /forms/v1/forms`) — paginate with `limit`/`offset`, and filter by creation date where supported.
2. **Read the form structure.** `get_form_forms_v1_forms__formId__get` returns the question set. For dropdown questions, resolve the option ids with `get_dropdown_question_options_forms_v1_forms__formId__questions__questionId__get` — submissions reference option ids, not labels, so you need this map before you can render answers.
3. **Pull submissions.** `get_form_submissions_forms_v1_forms__formId__form_submissions_get` over a date window, then `get_form_submission_forms_v1_forms__formId__form_submissions__formSubmissionId__get` for the full body of any submission you need in detail.
4. **Resolve attachments.** Answers that carry files reference a `fileId`. Call `get_file_url_attachments_v1_files__fileId__get` to get the metadata and download URL, and check the upload status field before fetching — uploads are asynchronous. Do **not** use `generate_download_url_attachments_v1_files_download_url_post`; it is flagged `deprecated: true` in the spec.
5. **Switch from polling to events.** Register `featureType: "forms"` with `create_webhook_settings_v1_webhooks_post`, passing the `formId` as `objectId` and subscribing to the `Form Submission` and `Form submission Edited` events. Then use the REST reads only to backfill.

## Rules

- **Edits are a separate event.** `Form submission Edited` fires independently of `Form Submission`. If you export to a warehouse, key on the submission id and upsert — do not append, or edited submissions will double-count.
- **Pagination**: `limit` default 10, `offset` default 0; iterate until a page returns fewer than `limit` items. Payloads sit under `data.<collection>`.
- **Rate limits**: per account. A nightly export across many forms must batch and pace itself against `x-ratelimit-day-remaining` (10,000/day on Expert), not just the minute budget.
- **Writing back**: form structure is mutable through `add_dropdown_options_forms_v1_forms__formId__questions__questionId__post`, `update_dropdown_options_forms_v1_forms__formId__questions__questionId__options__optionId__put` and `delete_dropdown_option_forms_v1_forms__formId__questions__questionId__options__optionId__delete`. Deleting an option that historical submissions reference will orphan those answers — prefer adding a new option.
- **Errors**: `422` for schema violations with `{"detail":[...]}`; `404` for an unknown form or submission id.

Cross-references: `asyncapi/connecteam-events-webhooks.yml`, `conventions/connecteam-conventions.yml`, `data-model/connecteam-data-model.yml`.
