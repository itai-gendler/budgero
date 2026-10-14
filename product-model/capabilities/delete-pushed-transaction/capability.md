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

# Delete pushed transaction

Delete a transaction a push client added earlier, referenced by that push's
message id.
