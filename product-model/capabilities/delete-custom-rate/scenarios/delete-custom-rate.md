---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a custom rate and confirms
  kind: actor
  actor: user
  entities:
  - {entity: custom-rate, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::currencies
- text: The Product removes the Custom rate; later conversions use fetched or manual rates
  kind: product
  actor: user
  entities:
  - {entity: custom-rate, effect: removes}
  contexts:
    web:
      place: web-app::signed-in::currencies
---

# Delete a custom rate

## Trigger

A pinned rate is no longer wanted.

## Outcome

The pair converts at fetched or manual rates again.
