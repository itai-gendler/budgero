---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to import while rows still need review
  kind: actor
  actor: user
  entities:
  - {entity: import-run, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::imports
- text: A row marked Needs review has no decision
  kind: condition
  entities:
  - {entity: transaction, effect: reads, facts: [Date]}
  contexts:
    web:
      place: web-app::signed-in::imports
- text: The Product keeps import unavailable and shows how many rows need a decision
  kind: product
  actor: user
  entities:
  - {entity: import-run, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::imports
---

# Hold an import until every possible duplicate is decided

## Trigger

A person skips the review of possible duplicates.

## Outcome

Nothing is imported until each is decided, one by one or all together.
