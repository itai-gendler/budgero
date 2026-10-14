---
kind: edge
routes:
  web: Web
steps:
- text: The User picks another fiat display currency
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in
- text: The Product saves the Budget's currency and reconverts every converted amount into it
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: changes, facts: [Display currency]}
  - {entity: transaction, effect: changes, facts: [Converted amount]}
  contexts:
    web:
      place: web-app::signed-in
---

# Change the display currency

## Trigger

A person moves country or wants to budget in another currency.

## Outcome

Every budget figure is shown in the new currency.

## Edge cases

- A cryptocurrency is refused as display currency.
