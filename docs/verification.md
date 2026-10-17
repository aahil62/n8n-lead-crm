# Verification and limitations

## Confirmed

A representative lead path passed through intake, AI signal extraction, deterministic scoring, Airtable state management, HubSpot contact/company/deal handling, and an Asana owner notification.

The workflow JSON is sanitized, parses successfully, has no credential blocks, contains no live account identifiers, and is exported inactive.

All 15 documented scenarios, including duplicate replay, returning leads, AI timeout, HubSpot 401 and 429, notification failure, follow-up dates and the weekly report, were run live in a sandbox on 2026-10-17. Results and execution IDs are in the [test report](test-report.md).

## Not yet claimed

The sandbox runs used fictional data, a HubSpot test account and forced failures (an invalid token, a local 429 mock, an invalid Asana project, a 1 ms AI timeout). They have not been repeated against a client's real field configuration, volumes or rate limits.

Do not describe the package as fully production-ready until the documented matrix passes against the target client's real field configuration and rate limits.

## Test assets

15 lead scenarios covering valid, duplicate, low-confidence, prompt-injection, CRM failure, and follow-up cases.

## Model-provider status

| Provider | Status |
|---|---|
| Groq-hosted model via an OpenAI-compatible endpoint | Used for the live test runs |
| OpenAI | Compatible with the same node configuration; test before claiming verified |
| Anthropic/Claude | Not verified in this package |
