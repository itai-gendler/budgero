---
domain: accounts
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/index.ts
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/split-service.ts
---

# Transaction

One movement of money in an account: a purchase, a paycheck, one leg of a
transfer. A transaction may be split into lines that each carry their own
category or transfer account.

## Information kept

- **Date** — the day it happened or is scheduled for
- **Inflow** — money coming in, in the account's currency
- **Outflow** — money going out, in the account's currency
- **Payee** — who was paid or who paid
- **Memo** — a free-text note
- **Category** — the category it is classified under, or the Transfers category for a transfer leg
- **Exchange rate** — the rate used to convert a foreign-currency amount, resolved or pinned by the person
- **Converted amount** — the amount in the budget's display currency, which drives budgeting
- **Split lines** — the lines of a split transaction, each with an amount, memo, payee and either a category or a transfer account
- **Transfer link** — the paired leg in the other account when it is a transfer
- **Label** — the label it carries, if any

## States

### Uncleared

Entered but not yet seen at the bank.

### Cleared

Seen at the bank; counts toward the cleared balance.

### Reconciled

Confirmed by a reconciliation; its cleared status is locked.
