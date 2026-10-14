---
entities:
- {entity: user, shows: [Master password set]}
references:
- kind: code
  role: implementation
  target: packages/app/src/app/startup/screens.tsx
---

# Master password

The gate between signing in and the budget data: creating the master password the first time, unlocking with it afterwards, or resetting Budgero when it is forgotten.
