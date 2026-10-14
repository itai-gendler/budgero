---
kind: primary
routes:
  web: Web
steps:
- text: The User renames a workspace they own
  kind: actor
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: The Product saves the Workspace name for every member
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: changes, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::workspaces
---

# Rename a workspace

## Trigger

A household renames its shared space.

## Outcome

Every member sees the new name.

## Edge cases

- An empty name is refused.
