---
domain: accounts
relations:
- {entity: transaction, verb: holds, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/accounts/index.ts
- kind: code
  role: implementation
  target: packages/core/src/services/accounts/types.ts
- kind: code
  role: implementation
  target: packages/app/src/entities/account/model/accountTypes.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/accounts.mdx
  title: Accounts
---

# Account

Where money physically lives: checking, savings, cash, a credit card, a loan,
an investment. On-budget accounts feed Ready to Assign and their spending hits
categories; off-budget accounts only track a balance.

## Information kept

- **Name** — the account name
- **Type** — Checking, Savings, Cash, Credit, Loan, Mortgage, Real Estate, Other Asset, Investment, Crypto or Retirement
- **Currency** — any supported fiat currency or cryptocurrency, independent of the budget's display currency
- **On budget** — whether the account takes part in the budget; Checking, Savings and Cash always do, Mortgage and the tracking asset types never do, Credit, Loan and Crypto are the person's choice
- **Balance** — the realized balance as of today, excluding future-dated transactions
- **Cleared balance** — the balance of cleared and reconciled transactions, which the bank statement should show
- **Reconciled at** — when the account was last reconciled
- **Original debt** — for a loan or mortgage, the total originally borrowed
- **Paid so far** — for a loan or mortgage, what had already been repaid when the account was added

## States

### Open

In day-to-day use and offered in pickers.

### Archived

Hidden from pickers and day-to-day lists; its transactions stay in history and reports.
