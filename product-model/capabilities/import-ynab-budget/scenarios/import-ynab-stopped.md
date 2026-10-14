---
kind: validation
routes:
  web: Web
steps:
- text: The User imports a YNAB plan or export ZIP
  kind: actor
  actor: user
  entities:
  - {entity: import-run, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: A transaction is missing or an account balance does not match
  kind: condition
  entities:
  - {entity: account, effect: reads, facts: []}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product stops the import and removes the incomplete Budget
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: [Name]}
  - {entity: import-run, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
---

# Stop a YNAB import that does not add up

## Trigger

The YNAB data cannot be reproduced faithfully.

## Outcome

No budget is left behind.
