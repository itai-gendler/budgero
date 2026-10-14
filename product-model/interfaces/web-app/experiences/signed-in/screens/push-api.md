---
entities:
- {entity: push-token, shows: [Enabled, Created at, Last used, Workspace]}
- {entity: push-message, shows: [Received at]}
entryPoints:
- web-app: /settings/api
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/push-api/PushApiPage.tsx
---

# Push API

The person's Push API token, the workspace key to give a push client, the push queue counts, and the IDs a push client needs.
