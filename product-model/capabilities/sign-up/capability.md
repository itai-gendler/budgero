---
availability:
- {place: 'web-app::signed-out'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/adapter/driving/http/handler/auth.go
  title: SelfHostRegister
- kind: code
  role: implementation
  target: packages/server/internal/config/registration.go
---

# Sign up

Register a local account on a self-hosted instance. Sign-up exists only on
self-hosted instances, and only while the instance's registration is enabled;
Budgero Cloud accounts are created with its identity provider.
