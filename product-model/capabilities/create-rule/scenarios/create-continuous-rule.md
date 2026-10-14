---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Create rule, names it, picks Continuous and adds conditions and actions
  kind: actor
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: The Product saves the enabled Rule
  kind: product
  actor: user
  entities:
  - {entity: rule, effect: creates, facts: [Name, Mode, Conditions, Actions, Run order, Enabled]}
  contexts:
    web:
      place: web-app::signed-in::rules
---

# Create a continuous rule

## Trigger

A person is tired of renaming the same bank payee by hand.

## Outcome

Every new matching transaction is cleaned up from now on.
