---
appliesTo:
- {type: capability, id: change-funding-priority}
- {type: capability, id: edit-category}
- {type: capability, id: create-category}
- {type: entity, id: category, facts: [Funding priority]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/goals/funding.ts
  title: isValidFundingPriority
---

# Funding priorities run from 1 Highest to 5 Lowest

With five levels, a category's funding priority is one of 1 Highest, 2 High,
3 Normal, 4 Low and 5 Lowest; switching to five levels lowers any higher number
to 5.
