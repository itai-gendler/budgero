---
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/app/startup/screens.tsx
- kind: code
  role: implementation
  target: packages/runtime/src/key-vault/key-vault.ts
---

# Unlock workspace

Unlock the encrypted budget data on a device with the master password, online
or offline.
