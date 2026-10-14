---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/goal-management/ui/GoalForm.tsx
- kind: code
  role: implementation
  target: packages/core/src/services/goals/index.ts
  title: GoalService.createGoal
- kind: code
  role: implementation
  target: packages/core/src/services/goals/calculations.ts
  title: GoalCalculations.validateGoal
---

# Create goal

Attach a goal to a category by choosing one of seven target types and its
amount, date or cadence.
