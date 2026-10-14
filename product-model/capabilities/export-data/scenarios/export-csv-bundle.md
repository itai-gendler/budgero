---
kind: primary
routes:
  web: Web
steps:
- text: The User picks a workspace and chooses Download CSV Files
  kind: actor
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::data-management
- text: The Product writes budgets, accounts, categories, category groups, transactions, assignments and goals into one CSV file each and downloads them zipped
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: [Name]}
  - {entity: transaction, effect: reads, facts: [Date, Inflow, Outflow, Payee, Memo, Category]}
  - {entity: assignment, effect: reads, facts: [Month, Amount]}
  - {entity: category-group, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  - {entity: goal, effect: reads, facts: []}
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::data-management
---

# Export a CSV bundle

## Trigger

A person needs their data for an accountant.

## Outcome

A plaintext copy is on the device, outside the encryption.
