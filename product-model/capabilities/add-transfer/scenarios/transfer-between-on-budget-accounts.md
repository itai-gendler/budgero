---
kind: primary
routes:
  web: Web
steps:
- text: The User enters a transfer between two accounts that both take part in budgeting
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records the outflow and inflow legs with a shared transfer link
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: source-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
  - {entity: transaction, as: destination-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: Ready to Assign and every category are unchanged
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Transfer between on-budget accounts

## Trigger

A person moves money from checking to savings.

## Outcome

Both account balances change and the budget does not.
