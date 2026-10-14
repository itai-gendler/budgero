---
entities:
- {entity: account, shows: [Name, Type, Currency, On budget, Balance, Cleared balance, Reconciled at], collects: [Name, Type, On budget]}
- {entity: transaction, shows: [Date, Payee, Memo, Category, Inflow, Outflow, Split lines, Converted amount], collects: [Date, Payee, Memo, Category, Inflow, Outflow, Split lines, Exchange rate]}
- {entity: occurrence, shows: [Due date]}
- {entity: category, shows: [Name]}
- {entity: payee, shows: [Name]}
entryPoints:
- web-app: /accounts/:accountId
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/accounts/AccountPage.tsx
---

# Account

One account's register: its balances, every transaction with its cleared status, the upcoming recurring and scheduled entries, and reconciliation.
