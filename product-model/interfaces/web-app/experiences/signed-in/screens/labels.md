---
entities:
- {entity: label, shows: [Name, Color], collects: [Name, Color]}
entryPoints:
- web-app: /settings/labels
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/LabelsPage.tsx
---

# Labels

The budget's labels and their colours.
