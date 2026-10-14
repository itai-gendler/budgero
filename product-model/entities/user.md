---
kind: person
acts: external
relations:
- {entity: workspace-membership, verb: holds, cardinality: one-to-many}
- {entity: push-token, verb: owns, cardinality: one-to-one}
- {entity: push-client, verb: connects, cardinality: one-to-one}
references:
- kind: code
  role: implementation
  target: packages/server/internal/domain/user.go
- kind: code
  role: implementation
  target: packages/server/internal/application/local_auth.go
---

# User

A signed-in person. A User reaches budgets through the workspaces they belong
to, as the owner of some and a member of others; what they may do in a
workspace depends on the role their membership names.

## Information kept

- **Name** — the name shown to other members of shared workspaces
- **Email** — the sign-in identity: the Budgero Cloud account email, or the username of a local account on a self-hosted instance
- **Master password set** — whether the person has created the master password their encryption keys are derived from
- **Workspace access** — whether the person may own workspaces: Granted on every self-hosted instance; on Budgero Cloud, Granted with an active subscription, trial, founding membership or beta access
