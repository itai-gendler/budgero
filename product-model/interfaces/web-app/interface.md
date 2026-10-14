---
type: web
actors:
- visitor
- user
entryPoints:
- web: /auth
- web: /budgeting
- web: /join
languages:
- en
- de
- fr
- es
- nl
references:
- kind: code
  role: implementation
  target: packages/app/src/app/router.tsx
- kind: doc
  role: context
  target: packages/app/README.md
  title: App README
---

# Budgero web app

The installable web app people budget in, on desktop and phone browsers. It
runs the budget locally in the browser, works offline, and synchronises
encrypted changes with the Budgero Cloud or a self-hosted server.
