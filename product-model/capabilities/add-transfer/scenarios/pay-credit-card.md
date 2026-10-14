---
kind: primary
routes:
  web: Web
steps:
- text: The User transfers money from checking into a credit card
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Type]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records both legs; the payment is a neutral transfer
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: source-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
  - {entity: transaction, as: destination-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The card's payment category shows the payment as activity and its Available drops
  kind: condition
  entities:
  - {entity: category, effect: reads, facts: [Activity, Available]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Pay a credit card

## Trigger

The card bill is due.

## Outcome

The card's debt falls and the payment category's set-aside money is used; no spending is counted twice.

## Edge cases

- Paying more than was set aside makes the payment category's Available negative, showing older debt being paid down.
