---
kind: configuration
of: business-rule
settings:
- {entity: budget, fact: Sharing within a priority}
takesEffect: At the next Fund Goals action after the setting is saved.
stability: Assignments already made by earlier funding stay as they are.
alternatives:
- id: proportional-shortfall-sharing
  selectedWhen: Sharing within a priority is Proportional shortfalls, the default.
- id: equal-completion-sharing
  selectedWhen: Sharing within a priority is Equal completion percentage.
---

# Goal funding sharing

Each budget chooses how Fund Goals shares money that runs out inside one
priority tier.
