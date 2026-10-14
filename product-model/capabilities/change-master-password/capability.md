---
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/SecurityPage.tsx
---

# Change master password

Replace the master password while keeping the data: the workspace keys are
re-wrapped under the new password and other devices are told to unlock again.
