---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Restore from Database File, picks a backup and confirms Yes, Replace All Data
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::data-management
- text: The Product replaces the workspace's budgets with the backup's, upgraded to the current format, and synchronises the result
  kind: product
  actor: user
  entities:
  - {entity: budget, as: current-budget, effect: removes}
  - {entity: budget, as: restored-budget, effect: creates, facts: [Name, Display currency, Icon, Number format, Ready to Assign mode, Priority choices, Sharing within a priority, Show priority badges]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::data-management
---

# Restore a database backup

## Trigger

A person needs to roll back to an earlier state.

## Outcome

Every member sees the restored data; other workspaces are not affected.

## Edge cases

- A backup from a newer app version asks the person to update first.
