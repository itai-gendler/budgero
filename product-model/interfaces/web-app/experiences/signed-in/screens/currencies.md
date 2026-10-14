---
entities:
- {entity: custom-rate, shows: [From currency, To currency, Rate, Start date, End date], collects: [From currency, To currency, Rate, Start date, End date]}
entryPoints:
- web-app: /settings/currencies
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/CurrencySettingsPage.tsx
---

# Currencies

Custom exchange rates for date ranges, and how long fetched rates are cached for offline use.
