---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a label
  kind: actor
  actor: user
  entities:
  - {entity: label, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::labels
- text: The Product takes the Label off every Transaction and deletes it
  kind: product
  actor: user
  entities:
  - {entity: label, effect: removes}
  - {entity: transaction, effect: changes, facts: [Label]}
  contexts:
    web:
      place: web-app::signed-in::labels
---

# Delete a label

## Trigger

A finished project no longer needs its label.

## Outcome

No transaction carries the label any more.
