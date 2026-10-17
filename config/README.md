# Configuration samples

The P1 qualification workflow reads scoring and routing rules from Airtable, so
the business can change them without editing the workflow.

- `scoring-config.sample.csv` seeds the `scoring_config` table: each active row
  adds `points` when a signal the AI extracted matches the rule.
- `routing-config.sample.csv` seeds the `routing_config` table: the owner,
  notification channel and booking link used for each route.

Column names must match the headers in these files exactly. See
[the Airtable schema guide](airtable-schema.md) and
[the data contract](../docs/data-contract.md) for field meanings. The rows are
fictional; review every rule, owner and link before testing.
