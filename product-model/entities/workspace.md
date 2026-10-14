---
domain: workspaces-and-sharing
relations:
- {entity: workspace-membership, verb: has, cardinality: one-to-many}
- {entity: invitation, verb: has, cardinality: one-to-many}
- {entity: budget, verb: contains, cardinality: one-to-many}
- {entity: push-message, verb: receives, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: packages/server/internal/domain/space.go
- kind: code
  role: implementation
  target: packages/server/internal/application/space_service.go
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/WorkspaceSettingsPage.tsx
- kind: doc
  role: intent
  target: packages/website/content/docs/sharing.mdx
  title: Sharing Budgets
---

# Workspace

A shared, end-to-end encrypted container of budgets. Everything inside a
workspace is encrypted with the workspace's key, which each member holds
wrapped under their own master password; the server routes the ciphertext but
never reads it.

## Information kept

- **Name** — the workspace name shown in the workspace list
- **Allow over-assignment** — whether assignments may take Ready to Assign below zero; off by default, and one setting for every budget in the workspace
