---
domain: budget
references:
- kind: code
  role: implementation
  target: packages/core/src/services/goals/types.ts
- kind: code
  role: implementation
  target: packages/core/src/services/goals/calculations.ts
- kind: code
  role: implementation
  target: packages/app/src/features/goal-management/ui/GoalForm.tsx
- kind: doc
  role: intent
  target: packages/website/content/docs/goals.mdx
  title: Goals
---

# Goal

A target attached to one category that turns it into a plan: Budgero computes
what the category needs this month and whether it is on track.

## Information kept

- **Target type** — one of Monthly Available Target, Monthly Allocation Target, Yearly Allocation Target, Yearly Available Target, Periodic Allocation Target, Periodic Available Target or Target Balance
- **Target amount** — the amount to have available or to assign, per month, per cycle or in total depending on the type
- **Start date** — when the goal, or for periodic targets its first cycle, starts
- **Target date** — the date a yearly target is due; for periodic targets the derived end of the first cycle
- **Repeats** — never, every year, or every N months from 2 to 120
- **Needed this month** — derived: what the category still needs assigned this month to stay on plan
- **Status** — derived each month: Not started, On track, Behind, At risk, Completed, Overfunded or Overspent
