---
appliesTo:
- {type: capability, id: create-goal}
- {type: capability, id: fund-goals}
- {type: entity, id: goal, facts: [Needed this month, Status]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/goals/calculations.ts
  title: GoalCalculations
- kind: doc
  role: intent
  target: packages/website/content/docs/goals.mdx
  title: How "needed this month" is computed
---

# Each target type computes what it needs this month its own way

A Monthly Available Target needs the target minus what was available before
this month's spending, so spending during the month creates no new need. A
Monthly Allocation Target needs the target minus this month's assignment. A
Yearly target and a Periodic target need this month's milestone: what is still
missing spread over the months left in the cycle, a periodic amount spread
evenly over its cycle. A Target Balance needs the target minus the category's
Available. A goal is Overspent when its category is negative, and a Monthly
Available Target is Overfunded above 120% of its target.
