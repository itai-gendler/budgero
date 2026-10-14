---
domain: rules
references:
- kind: code
  role: implementation
  target: packages/core/src/services/rules/index.ts
  title: RuleService.executeRule
---

# Rule run

One execution of a rule, with every change it made, shown in the rule's run
history.

## Information kept

- **Trigger** — Run now, Retro run or Continuous
- **Evaluated** — how many transactions it looked at
- **Changed** — how many transactions it changed
- **Changes** — each changed transaction with the values before and after
- **Errors** — transactions it could not change and why

## States

### Completed

Finished; its changes are in place.

### Undone

Its changes were reverted.
