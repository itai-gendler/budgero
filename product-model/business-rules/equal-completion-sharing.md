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

# Limited money brings the least-funded goals to one completion percentage

When money runs out inside one priority tier, the categories furthest from
this month's requirement are raised together toward one common completion
percentage, without taking money already assigned. A tier holding a goal whose
monthly requirement is not positive is shared by proportional shortfalls
instead.
