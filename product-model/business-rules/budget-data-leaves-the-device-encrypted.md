---
appliesTo:
- {type: capability, id: set-master-password}
- {type: capability, id: change-master-password}
- {type: capability, id: redeem-invite}
- {type: capability, id: create-invite}
- {type: entity, id: workspace}
references:
- kind: code
  role: implementation
  target: packages/runtime/src/crypto/space-key-crypto.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/security.mdx
  title: Security model
---

# Budget data leaves the device only encrypted

Everything in a workspace is encrypted on the device before it is synchronised.
The master password never leaves the device; the server stores only
ciphertext, each member's copy of the workspace key wrapped under their own
master password, and the hash of an invitation's secret.
