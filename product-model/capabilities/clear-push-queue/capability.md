---
domain: push-api
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/adapter/driving/http/handler/push.go
  title: ClearPushQueue
---

# Clear push queue

Remove pending push messages without applying them.
