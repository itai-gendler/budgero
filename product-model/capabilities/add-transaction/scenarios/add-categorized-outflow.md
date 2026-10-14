---
kind: primary
routes:
  web: Web
steps:
- text: The User enters a purchase with date, payee, category, memo and outflow
  kind: actor
  actor: user
  entities:
  - {entity: payee, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records the uncleared Transaction and updates the Account's balance
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount]}
  - {entity: account, effect: reads, facts: [Balance]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product runs the budget's enabled continuous rules on the new transaction
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: [Payee, Memo, Category]}
  - {entity: rule, effect: reads, facts: []}
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The category's Activity and Available reflect the purchase
  kind: condition
  entities:
  - {entity: category, effect: reads, facts: [Activity, Available]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Add a categorised purchase

## Trigger

A person spends money and records it.

## Outcome

The purchase is in the register and the category shows less available.
