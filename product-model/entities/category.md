---
domain: budget
relations:
- {entity: assignment, verb: has, cardinality: one-to-many}
- {entity: goal, verb: has, cardinality: one-to-one}
- {entity: transaction, verb: classifies, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/categories/index.ts
- kind: code
  role: implementation
  target: packages/core/src/services/monthly-budgets/queries.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/categories.mdx
  title: Categories
---

# Category

A job for money: Groceries, Rent, Vacation. Each month a category shows what
was assigned to it, the activity recorded against it, and what is still
available. Income categories sit in the Income group; a credit card's payment
category and a loan's linked category are kept for their account.

## Information kept

- **Name** — the category name; unique among income categories
- **Group** — the category group it sits in
- **Funding priority** — the order Fund Goals serves it in; lower numbers first, 3 (Normal) by default
- **Exclude from budget pace** — whether it is left out of the month-progress pace indicators
- **Activity** — derived: net spending and inflows recorded in it for the month on on-budget accounts
- **Available** — derived: the balance carried from earlier months plus this month's assignment minus this month's activity
- **Linked account** — the credit card or loan whose payments it tracks, when it is a payment or linked category
