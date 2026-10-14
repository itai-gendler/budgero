---
appliesTo:
- {type: capability, id: sign-up}
- {type: capability, id: sign-in}
references:
- kind: code
  role: implementation
  target: packages/server/internal/config/registration.go
- kind: doc
  role: context
  target: docs/selfhost-cli.md
  title: Self-host CLI
---

# Self-hosted sign-up works only while registration is enabled

An instance operator can disable registration; while it is disabled every sign-up is refused and only existing local accounts sign in.
