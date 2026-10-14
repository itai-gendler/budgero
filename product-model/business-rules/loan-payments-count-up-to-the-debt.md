---
appliesTo:
- {type: capability, id: add-transfer}
- {type: capability, id: mark-occurrence-ready}
references:
- kind: doc
  role: intent
  target: packages/website/content/docs/debt-tracking.mdx
  title: The spending cap
---

# A loan payment counts as spending only up to the debt owed

A transfer into an on-budget loan or mortgage counts as spending in its linked
category up to what is owed; anything beyond is recorded as a plain transfer.
Payments to off-budget debts are always neutral transfers.
