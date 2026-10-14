---
entities:
- {entity: user, shows: [Master password set]}
entryPoints:
- web-app: /settings/security
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/SecurityPage.tsx
---

# Security and privacy

Changing the master password and how long it is remembered on this device.
