---
domain: budget
relations:
- {entity: category, verb: contains, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/categories/index.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/category-groups.mdx
  title: Category Groups
---

# Category group

A named shelf of categories in the budget table. Every budget has the system
groups Income, Uncategorized and Transfers; Credit Card Payments and
Liabilities appear when the first credit card or loan is added.

## Information kept

- **Name** — the group name
- **Position** — its place among the groups of the budget table
- **System group** — whether Budgero manages the group (Income, Uncategorized, Transfers, Credit Card Payments, Liabilities)
