---
availability:
- {place: 'web-app::signed-out'}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/auth/AuthPage.tsx
- kind: code
  role: implementation
  target: packages/server/internal/adapter/driving/http/handler/auth.go
  title: SelfHostLogin
---

# Sign in

Sign in to Budgero. Budgero Cloud uses a Budgero account; a self-hosted
instance uses local accounts on that instance.
