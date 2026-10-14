---
appliesTo:
- {type: capability, id: create-account}
- {type: entity, id: transaction}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/accounts/index.ts
  title: AccountService.createAccount
---

# An asset's starting balance is income; a debt's opening balance stays outside the budget

A new asset account's starting balance is an Initial Balance inflow in the
Income category, so on budget it is assignable at once. A debt account's
opening debt and payments so far are recorded in the Transfers category and
change neither categories nor Ready to Assign.
