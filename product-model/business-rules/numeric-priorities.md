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

# Funding priorities are any positive whole number

In numeric mode a category's funding priority is any positive whole number,
entered and applied directly.
