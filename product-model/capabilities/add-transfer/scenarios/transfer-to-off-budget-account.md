---
kind: primary
routes:
  web: Web
steps:
- text: The User transfers money to a tracking asset account such as an investment
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [On budget]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records both legs in the Transfers category
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: source-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
  - {entity: transaction, as: destination-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: Ready to Assign falls by the amount
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Transfer money off the budget

## Trigger

A person moves money into an investment account.

## Outcome

The money leaves the budget; moving money back from that account raises Ready to Assign.

## Edge cases

- Categorising the on-budget leg to a spending category makes it spending in that category instead of lowering Ready to Assign.
