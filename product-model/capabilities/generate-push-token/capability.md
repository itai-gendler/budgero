---
domain: push-api
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/push_token.go
  title: GeneratePushTokenUsecase.Execute
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/push-api/TokenActions.tsx
---

# Generate push token

Generate the Push API token for the person's default workspace, or regenerate
it, which replaces the previous token. The token is shown once.
