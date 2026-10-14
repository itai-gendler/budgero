---
kind: primary
routes:
  web: Web
steps:
- text: The User creates a budget with starter categories turned off
  kind: actor
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product creates the Budget with only the Income, Uncategorized and Transfers groups, each with a category of the same name
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: creates, facts: [Name, Display currency, Icon, Number format, Ready to Assign mode, Priority choices, Sharing within a priority, Show priority badges]}
  - {entity: category-group, effect: creates, facts: [Name, Position, System group], with: budget}
  - {entity: category, effect: creates, facts: [Name, Group, Funding priority, Exclude from budget pace], with: category-group}
  contexts:
    web:
      place: web-app::signed-in
---

# Create a budget without starter categories

## Trigger

A person will build their own structure or import one.

## Outcome

The budget holds only the system groups.
