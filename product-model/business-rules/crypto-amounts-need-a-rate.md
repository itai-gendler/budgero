---
appliesTo:
- {type: capability, id: add-transaction}
- {type: capability, id: add-transfer}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/index.ts
  title: TransactionService.addTransaction
---

# A cryptocurrency amount is never converted without a rate

A transaction in a cryptocurrency account is refused when no exchange rate to
the display currency is known; a fiat amount without a rate is converted 1:1,
marked pending and reconverted later.
