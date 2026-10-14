---
domain: payees
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/payee-service.ts
---

# Payee

A name in the budget's payee directory: saved by hand or taken from
transactions, offered when entering transactions.

## Information kept

- **Name** — the payee name, unique ignoring case
- **Usage count** — derived: how many transactions carry it
