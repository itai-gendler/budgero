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

# Push transaction

Send a new income or expense into the default workspace from another system,
optionally split across categories, as an encrypted push. It is applied the
next time a member's app processes the push queue.
