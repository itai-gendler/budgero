---
entities:
- {entity: user, collects: [Email]}
entryPoints:
- web-app: /auth
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/auth/AuthPage.tsx
---

# Sign in

Where a visitor signs in, or registers a local account on a self-hosted instance that allows it.
