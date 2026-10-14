---
appliesTo:
- {type: capability, id: fund-goals}
- {type: entity, id: budget, facts: [Sharing within a priority]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/goals/funding.ts
  title: allocateGoalFunding
---

# Limited money covers the same fraction of each shortfall

When money runs out inside one priority tier, each category of the tier
receives the same fraction of what it still needs this month.
