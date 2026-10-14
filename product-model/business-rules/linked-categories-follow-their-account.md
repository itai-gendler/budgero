---
appliesTo:
- {type: capability, id: delete-category}
- {type: capability, id: archive-account}
- {type: capability, id: unarchive-account}
- {type: capability, id: delete-account}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/categories/index.ts
  title: CategoryService.deleteCategory
- kind: code
  role: implementation
  target: packages/core/src/services/accounts/index.ts
  title: AccountService.setAccountArchived
---

# A payment or linked category is kept while its account is active

A credit card's payment category and a loan's linked category cannot be
deleted while the account is open; archiving the account releases it,
unarchiving relinks or recreates it, and deleting the account deletes it.
