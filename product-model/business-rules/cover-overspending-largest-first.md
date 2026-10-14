---
appliesTo:
- {type: capability, id: cover-overspending}
- {type: entity, id: category, facts: [Available]}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/assign-dropdown/assign-dropdown.utils.ts
  title: prepareOverspentAssignments
---

# Overspending is covered largest first

Cover Overspending tops up overspent categories in order of how far they are
overspent, largest first, each back to zero, until Ready to Assign is used up.
