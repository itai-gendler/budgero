---
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/app/startup/screens.tsx
- kind: code
  role: implementation
  target: packages/runtime/src/crypto/space-key-crypto.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/master-password.mdx
  title: Master Password
---

# Set master password

Create the master password the person's encryption keys are derived from. It
never leaves the device.
