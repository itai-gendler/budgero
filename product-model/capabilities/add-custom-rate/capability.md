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
  target: packages/core/src/services/currency/index.ts
---

# Add custom rate

Pin an exchange rate for a currency pair over a date range; transactions in that
range are recalculated with it.
