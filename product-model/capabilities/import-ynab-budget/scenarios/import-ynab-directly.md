---
kind: primary
routes:
  web: Web
steps:
- text: The User enters a YNAB personal access token and picks a plan
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in
- text: The Product reads the plan from YNAB with the token held only in memory
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in
- text: The Product creates the Budget with its accounts, categories, transactions, splits, transfers and monthly assignments
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: creates, facts: [Name, Display currency, Icon, Number format, Ready to Assign mode, Priority choices, Sharing within a priority, Show priority badges]}
  - {entity: category-group, effect: creates, facts: [Name, Position, System group], with: budget}
  - {entity: account, effect: creates, to: Open, facts: [Name, Type, Currency, On budget, Balance], with: budget}
  - {entity: category, effect: reads, facts: []}
  - {entity: assignment, effect: reads, facts: []}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product compares every transaction, account balance, category month and Ready to Assign month with YNAB and records the Import
  kind: product
  actor: user
  entities:
  - {entity: import-run, effect: creates, to: Completed, facts: [Source, Imported at, Transactions created, Accounts created, Categories created]}
  - {entity: category, effect: reads, facts: []}
  - {entity: account, effect: reads, facts: []}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
---

# Import a YNAB plan by connecting directly

## Trigger

A person moves from YNAB.

## Outcome

The budget matches YNAB and is ready to use.
