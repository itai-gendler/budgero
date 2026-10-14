---
kind: edge
routes:
  web: Web
steps:
- text: The User transfers money from checking into a loan
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Type, Balance]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records both legs
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: source-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
  - {entity: transaction, as: destination-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The payment counts as spending in the loan's linked category up to the debt owed; any overpayment is a plain transfer
  kind: condition
  entities:
  - {entity: category, effect: reads, facts: [Activity, Linked account]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Pay a loan

## Trigger

A person makes the monthly loan payment.

## Outcome

The loan balance falls and the linked category shows the payment as spending.
