---
domain: push-api
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/push-api/EncryptionInfoPanel.tsx
---

# Reveal encryption key

Show the default workspace's encryption key, which a push client needs to
encrypt its operations.
