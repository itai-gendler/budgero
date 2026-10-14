---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a category with a name to a category group
  kind: actor
  actor: user
  entities:
  - {entity: category-group, effect: reads, facts: [Name]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product creates the Category in that group at the default funding priority
  kind: product
  actor: user
  entities:
  - {entity: category, effect: creates, facts: [Name, Group, Funding priority, Exclude from budget pace]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Create a category in a group

## Trigger

A person needs a new job for money.

## Outcome

The category appears in its group with nothing assigned.
