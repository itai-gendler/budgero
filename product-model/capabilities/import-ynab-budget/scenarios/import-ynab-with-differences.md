---
kind: edge
routes:
  web: Web
steps:
- text: The User imports a YNAB plan
  kind: actor
  actor: user
  entities:
  - {entity: import-run, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: Category history or Ready to Assign differs from YNAB
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product shows the affected months and amounts
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in
- text: The User chooses Import anyway
  kind: actor
  actor: user
  entities:
  - {entity: import-run, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product keeps the Budget and records the Import with its accepted warnings
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: creates, facts: [Name, Display currency, Icon, Number format, Ready to Assign mode, Priority choices, Sharing within a priority, Show priority badges]}
  - {entity: import-run, effect: creates, to: Completed with warnings, facts: [Source, Imported at, Transactions created, Accounts created, Categories created, Warnings], with: budget}
  contexts:
    web:
      place: web-app::signed-in
---

# Keep a YNAB import despite differences

## Trigger

A YNAB budget has history Budgero calculates differently.

## Outcome

The budget is kept and the warnings stay visible in the import history.

## Edge cases

- Choosing to remove the import deletes the incomplete budget.
