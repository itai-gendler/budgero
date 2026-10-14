---
appliesTo:
- {type: capability, id: add-transaction}
- {type: capability, id: add-custom-rate}
- {type: entity, id: custom-rate}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/currency/index.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/accounts.mdx
  title: Multi-currency accounts
---

# Custom rates come first when converting

A foreign-currency amount converts at the rate entered on the transaction if
there is one, otherwise at a custom rate covering its date, then the fetched
daily rate, then a manual rate, then the nearest earlier cached rate.
