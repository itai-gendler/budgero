---
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/user_service.go
  title: UserService.ResetData
- kind: code
  role: implementation
  target: packages/app/src/app/service-guard/service-guard.utils.ts
  title: handleAccountReset
- kind: doc
  role: intent
  target: packages/website/content/docs/master-password.mdx
  title: Forgotten password = lost data
---

# Reset master password

Start over when the master password is forgotten: everything encrypted under
it is deleted, because nobody can decrypt it.
