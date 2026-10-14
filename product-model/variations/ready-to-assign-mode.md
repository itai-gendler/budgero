---
kind: configuration
of: business-rule
settings:
- {entity: budget, fact: Ready to Assign mode}
takesEffect: Immediately when the setting is saved; every figure is recalculated from the same transactions and assignments.
stability: Switching is non-destructive and can be reversed at any time; nothing recorded changes.
alternatives:
- id: ready-to-assign-cumulative
  selectedWhen: Ready to Assign mode is Cumulative, the default for every budget.
- id: ready-to-assign-monthly
  selectedWhen: Ready to Assign mode is Monthly.
---

# Ready to Assign mode

Each budget chooses whether Ready to Assign is one continuous pool or is
reckoned month by month, as people moving from YNAB expect; both are
supported.
