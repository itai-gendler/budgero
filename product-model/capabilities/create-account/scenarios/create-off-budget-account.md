---
kind: primary
routes:
  web: Web
steps:
- text: The User adds an Investment account with a starting balance
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product creates the Account off budget with an opening Transaction
  kind: product
  actor: user
  entities:
  - {entity: account, effect: creates, to: Open, facts: [Name, Type, Currency, On budget, Balance]}
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Inflow, Memo, Category, Converted amount], with: account}
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: Ready to Assign is unchanged
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in
---

# Create an off-budget tracking account

## Trigger

A person wants net worth to include a retirement or investment account.

## Outcome

The account counts toward net worth but never toward the budget.
