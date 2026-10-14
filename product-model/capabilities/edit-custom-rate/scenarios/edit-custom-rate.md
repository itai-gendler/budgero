---
kind: primary
routes:
  web: Web
steps:
- text: The User edits a custom rate
  kind: actor
  actor: user
  entities:
  - {entity: custom-rate, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::currencies
- text: The Product saves the Custom rate and recalculates affected transactions
  kind: product
  actor: user
  entities:
  - {entity: custom-rate, effect: changes, facts: [Rate, Start date, End date]}
  - {entity: transaction, effect: changes, facts: [Exchange rate, Converted amount]}
  contexts:
    web:
      place: web-app::signed-in::currencies
---

# Edit a custom rate

## Trigger

A rate was entered wrongly.

## Outcome

Affected transactions convert at the corrected rate.
