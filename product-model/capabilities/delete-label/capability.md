---
domain: labels
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/label-service.ts
  title: LabelService.deleteLabel
---

# Delete label

Delete a label and take it off every transaction.
