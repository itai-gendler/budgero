---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Reset Budgero and types RESET to confirm
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The Product deletes every Workspace the User owns, with its budgets and memberships
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: removes}
  - {entity: budget, effect: removes, with: workspace}
  - {entity: workspace-membership, as: owned-workspace-membership, effect: removes, with: workspace}
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The Product removes the User's Membership in each workspace shared with them
  kind: product
  actor: user
  entities:
  - {entity: workspace-membership, as: shared-membership, effect: removes}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The Product clears the User's master password and the data on the device
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Master password set]}
  contexts:
    web:
      place: web-app::signed-in::master-password
---

# Reset Budgero after forgetting the master password

## Trigger

A person cannot remember their master password.

## Outcome

They can use Budgero again with a fresh master password; their former data is gone for good, including for the members of workspaces they owned.
