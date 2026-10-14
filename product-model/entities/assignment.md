---
domain: budget
references:
- kind: code
  role: implementation
  target: packages/core/src/services/monthly-budgets/index.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/assign-money.mdx
  title: Assigning Money
---

# Assignment

The money given to one category for one month: the Assigned figure in the
budget table. Assigning draws from Ready to Assign; lowering an assignment
returns the difference to it.

## Information kept

- **Month** — the month it funds
- **Amount** — the amount assigned; may be negative
- **Category** — the category it funds
