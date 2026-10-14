---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Create New Budget and enters a name, fiat display currency, icon and number format, keeping starter categories
  kind: actor
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product creates the Budget with Cumulative Ready to Assign and default funding settings, its Income, Uncategorized and Transfers groups and the Frequent, Non-Monthly, Goals and Quality of Life groups with their categories
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: creates, facts: [Name, Display currency, Icon, Number format, Ready to Assign mode, Priority choices, Sharing within a priority, Show priority badges]}
  - {entity: category-group, effect: creates, facts: [Name, Position, System group], with: budget}
  - {entity: category, effect: creates, facts: [Name, Group, Funding priority, Exclude from budget pace], with: category-group}
  - {entity: goal, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product switches to the new budget
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in
---

# Create a budget with starter categories

## Trigger

A person starts a new budget from scratch.

## Outcome

The new budget is open with starter categories ready for assigning.
