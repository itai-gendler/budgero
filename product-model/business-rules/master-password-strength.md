---
appliesTo:
- {type: capability, id: set-master-password}
- {type: entity, id: user, facts: [Master password set]}
references:
- kind: code
  role: implementation
  target: packages/app/src/app/startup/screens.tsx
---

# Setting up a master password requires a strong password

A master password is set only when it has at least 12 characters with an uppercase letter, a lowercase letter, a number and a special character, and its confirmation matches.
