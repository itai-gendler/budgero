---
entities:
- {entity: payee, shows: [Name, Usage count], collects: [Name]}
entryPoints:
- web-app: /settings/payees
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/PayeesPage.tsx
---

# Payees

The budget's payee directory with how often each payee is used.
