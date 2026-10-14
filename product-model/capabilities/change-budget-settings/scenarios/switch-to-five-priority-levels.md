---
kind: edge
routes:
  web: Web
steps:
- text: The User switches Priority choices from Numeric to Five levels
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget-settings
- text: The Product saves the setting and lowers every category priority above 5 to 5 in the same undoable change
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: changes, facts: [Priority choices]}
  - {entity: category, effect: changes, facts: [Funding priority]}
  contexts:
    web:
      place: web-app::signed-in::budget-settings
---

# Switch funding priorities back to five levels

## Trigger

A person stops using custom numeric priorities.

## Outcome

Every category priority is between 1 and 5.

## Edge cases

- Switching to Numeric keeps every priority as it is.
