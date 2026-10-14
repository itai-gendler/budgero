---
appliesTo:
- {type: capability, id: push-transaction}
- {type: capability, id: update-pushed-transaction}
- {type: capability, id: delete-pushed-transaction}
- {type: capability, id: push-transfer}
- {type: capability, id: delete-pushed-transfer}
- {type: capability, id: process-push-queue}
- {type: entity, id: push-message}
references:
- kind: code
  role: implementation
  target: packages/app/src/shared/runtime/app-runtime.ts
  title: AppRuntime.processPushQueue
- kind: doc
  role: intent
  target: packages/website/content/docs/push-api.mdx
  title: Encryption requirements
---

# The server never reads a pushed operation

A push client encrypts every operation with the workspace key before sending
it; the server only queues it, and a member's app decrypts and applies it on the
device. A message that does not decrypt with the workspace key fails without
changing anything.
