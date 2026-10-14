---
kind: primary
routes:
  web: Web
steps:
- text: The User adds an income category with a name in the budget settings
  kind: actor
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget-settings
- text: The Product creates the Category in the Income group
  kind: product
  actor: user
  entities:
  - {entity: category, effect: creates, facts: [Name, Group, Funding priority, Exclude from budget pace]}
  - {entity: category-group, effect: reads, facts: [System group]}
  contexts:
    web:
      place: web-app::signed-in::budget-settings
---

# Create an income category

## Trigger

A person wants to tell income sources apart, such as salary and freelance work.

## Outcome

Inflows categorised to the new category count as income for Ready to Assign.
