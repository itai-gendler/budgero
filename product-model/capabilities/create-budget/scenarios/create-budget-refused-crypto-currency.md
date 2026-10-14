---
kind: validation
routes:
  web: Web
steps:
- text: The User creates a budget with a cryptocurrency as display currency
  kind: actor
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product refuses because the display currency must be fiat
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: [Display currency]}
  contexts:
    web:
      place: web-app::signed-in
---

# Refuse a cryptocurrency as display currency

## Trigger

A person wants to budget in bitcoin.

## Outcome

No budget is created; crypto stays available as an account currency.

## Edge cases

- An empty name, currency, icon or number format is refused as well.
