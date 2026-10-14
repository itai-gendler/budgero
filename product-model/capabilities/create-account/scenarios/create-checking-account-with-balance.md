---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a Checking account with a name, currency and starting balance
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product creates the on-budget Account with an Initial Balance inflow Transaction in the Income category
  kind: product
  actor: user
  entities:
  - {entity: account, effect: creates, to: Open, facts: [Name, Type, Currency, On budget, Balance]}
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Inflow, Memo, Category, Converted amount], with: account}
  - {entity: category, effect: reads, facts: [Name]}
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: Ready to Assign rises by the starting balance
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in
---

# Create a checking account with a starting balance

## Trigger

A person starts tracking the account their salary lands in.

## Outcome

The account shows its balance and that money is immediately assignable.
