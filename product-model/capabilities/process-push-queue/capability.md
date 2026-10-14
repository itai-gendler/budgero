---
domain: push-api
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/shared/runtime/app-runtime.ts
  title: AppRuntime.processPushQueue
- kind: code
  role: implementation
  target: packages/app/src/app/startup/StartupController.tsx
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/push-api/usePushApiState.ts
---

# Process push queue

Apply pending push messages to the workspace: automatically when a member's
app opens the workspace and finishes its first sync, or on demand from the
Push API settings.
