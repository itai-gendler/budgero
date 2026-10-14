---
kind: configuration
of: business-rule
settings:
- {entity: budget, fact: Priority choices}
takesEffect: Immediately when the setting is saved.
stability: Switching to five levels lowers priorities above 5 to 5 in the same undoable change; switching to numeric keeps every priority.
alternatives:
- id: five-level-priorities
  selectedWhen: Priority choices is Five levels, the default.
- id: numeric-priorities
  selectedWhen: Priority choices is Numeric.
---

# Funding priority choices

Each budget chooses between five named funding priorities and any positive
number.
