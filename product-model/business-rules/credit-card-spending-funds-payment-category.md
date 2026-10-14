---
appliesTo:
- {type: capability, id: add-transaction}
- {type: capability, id: add-transfer}
- {type: entity, id: category, facts: [Available]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/monthly-budgets/index.ts
  title: MonthlyBudgetService.getMonthlyBudget
- kind: doc
  role: intent
  target: packages/website/content/docs/debt-tracking.mdx
  title: Credit Card Payment categories
---

# Budgeted credit card spending funds the card's payment category

When a category is spent on an on-budget credit card, the part the category
had available moves into that card's payment category; spending beyond it
becomes card debt. When several cards spend in one category, the funded amount
is split between their payment categories by each card's share of the
spending. A payment to the card is the payment category's activity.
