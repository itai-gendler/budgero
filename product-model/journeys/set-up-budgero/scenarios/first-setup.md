---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User sets a master password
  kind: actor
  actor: user
  capability: set-master-password
  entities:
  - {entity: user, effect: changes, facts: [Master password set]}
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The Product carries the User to creating a first workspace because they belong to none
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in
- text: The User names the workspace
  kind: actor
  actor: user
  capability: create-workspace
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product creates the Workspace with the User as owner
  kind: product
  actor: user
  capability: create-workspace
  entities:
  - {entity: workspace, effect: creates, facts: [Name, Allow over-assignment]}
  - {entity: workspace-membership, effect: creates, facts: [Role, Joined at], with: workspace}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product carries the User to creating a budget because the workspace holds none
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: []}
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The User enters the budget's name and display currency
  kind: actor
  actor: user
  capability: create-budget
  entities:
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product creates the Budget with its system groups
  kind: product
  actor: user
  capability: create-budget
  entities:
  - {entity: budget, effect: creates, facts: [Name, Display currency, Icon, Number format, Ready to Assign mode, Priority choices, Sharing within a priority, Show priority badges]}
  - {entity: category-group, effect: creates, facts: [Name, Position, System group], with: budget}
  contexts:
    web:
      place: web-app::signed-in
---

# Set up Budgero for the first time

## Trigger

A person with workspace access signs in for the first time.

## Outcome

The budget table is open and ready for the first assignment.
