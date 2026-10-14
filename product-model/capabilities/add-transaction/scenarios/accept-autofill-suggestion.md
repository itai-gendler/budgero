---
kind: edge
routes:
  web: Web
steps:
- text: The User starts entering a transaction
  kind: actor
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product finds an enabled Autofill Rule matching the payee or memo and suggests its category, payee, memo or account without changing anything
  kind: product
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: [Conditions, Actions]}
  - {entity: payee, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The User accepts the suggestions and saves the transaction
  kind: actor
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records the Transaction with the accepted values
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Accept an autofill suggestion

## Trigger

A person enters a fuel purchase at the pump.

## Outcome

The form was filled in two taps; rejected suggestions were not applied.

## Edge cases

- Once a suggestion is applied, autofill stops suggesting for that entry.
