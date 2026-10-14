---
domain: currencies
references:
- kind: code
  role: implementation
  target: packages/core/src/services/currency/index.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/multi-currency.mdx
  title: Multi-currency
---

# Custom rate

An exchange rate a person pins for a currency pair over a date range, which
takes priority over fetched and manual rates.

## Information kept

- **From currency** — the currency converted from
- **To currency** — the currency converted into
- **Rate** — the exchange rate
- **Start date** — the first day it applies
- **End date** — the last day it applies; open-ended when empty
