---
domain: push-api
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/adapter/driving/http/handler/push.go
  title: TogglePushToken
---

# Enable push token

Turn the Push API token back on.
