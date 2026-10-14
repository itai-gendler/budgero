---
appliesTo:
- {type: capability, id: fund-goals}
- {type: entity, id: category, facts: [Funding priority]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/goals/funding.ts
  title: allocateGoalFunding
- kind: doc
  role: intent
  target: packages/website/content/docs/goals.mdx
  title: Category funding priorities
---

# Fund Goals serves lower priority numbers first

Fund Goals fully covers every underfunded goal of one funding priority before
moving to the next higher number, whatever the categories' position or group.
Categories without goals keep their priority but receive nothing. Amounts are
exact to the milliunit, and ties are broken by category, never by order on the
screen.
