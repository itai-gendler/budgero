---
domain: currencies
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/CurrencySettingsPage.tsx
- kind: code
  role: implementation
  target: packages/core/src/services/user-meta/index.ts
---

# Change currency settings

Choose how long fetched exchange rates are cached for offline use and whether
rates entered offline are replaced by the official rate once back online.
