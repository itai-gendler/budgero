---
appliesTo:
- {type: capability, id: delete-account}
- {type: entity, id: account}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/account-management/ui/EditAccountDialog.tsx
  title: handleDelete
---

# Only accounts without transactions are deleted

An account is deleted only when it holds no transactions and its balance is zero; any other account is archived instead.
