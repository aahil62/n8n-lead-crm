# Airtable schema guide

Use fictional data while configuring the package. Exact field types and state
semantics are documented in [the data contract](../docs/data-contract.md).

| Table | Purpose | Key fields |
|---|---|---|
| leads | Canonical lead and CRM state | idempotency_key, email, intent, score, route, crm_sync_status, follow_up_at, reminder_sent_at (date/time; needed by the follow-up sweeper) |
| scoring_config | Business-editable score rules | field, operator, expected_value, points, active |
| routing_config | Owner and notification channel per route | condition, owner_id, notification_channel, calendar_link, active |
| review_queue | Low-confidence or unsafe cases | correlation_id, reason, status, reviewer, reviewed_at |
| execution_audit | Sanitized run history | correlation_id, workflow, stage, status, timestamps |
| dead_letter | Recoverable failure context | correlation_id, failed_stage, retryable, sanitized_input, status |

Column names must match exactly: the P1-02 workflow reads `field`, `operator`,
`expected_value`, `points` and `active` from `scoring_config`, and `condition`,
`owner_id`, `notification_channel`, `calendar_link` and `active` from
`routing_config`. If no active scoring rows are found, P1-02 falls back to its
built-in default rules. Score bands (hot ≥ 70, warm ≥ 40) and follow-up timing
(1 day for qualified, 7 days for nurture) are set in the P1-02 code nodes.
