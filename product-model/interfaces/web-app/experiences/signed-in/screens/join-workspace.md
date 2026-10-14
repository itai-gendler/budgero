---
entities:
- {entity: invitation, collects: [Invite link]}
entryPoints:
- web-app: /join
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/JoinWorkspacePage.tsx
---

# Join workspace

Where an invite link lands: the invite code and the master password needed to take the shared workspace key.
