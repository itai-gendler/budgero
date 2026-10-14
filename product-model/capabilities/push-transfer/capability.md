---
domain: push-api
availability:
- {place: push-api}
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/adapter/driving/http/handler/push.go
  title: PushMutation
- kind: code
  role: implementation
  target: packages/app/src/shared/runtime/app-runtime.ts
  title: AppRuntime.processPushQueue
- kind: doc
  role: intent
  target: packages/website/content/docs/push-api.mdx
  title: Supported operations today
---

# Push transfer

Send a linked transfer between two of the workspace's accounts, identified by a
transfer id the client chooses.
