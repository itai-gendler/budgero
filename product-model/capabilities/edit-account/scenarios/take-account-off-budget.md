---
kind: primary
routes:
  web: Web
steps:
- text: The User switches a credit card or loan to tracking only
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product saves the Account as a tracking account
  kind: product
  actor: user
  entities:
  - {entity: account, effect: changes, facts: [On budget]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: Its transactions no longer count in categories or Ready to Assign
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  - {entity: category, effect: reads, facts: [Activity]}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Take an account off budget

## Trigger

A person only wants to see a debt's balance, not budget for it.

## Outcome

The account is tracked off budget; its payments become neutral transfers.

## Edge cases

- Checking, Savings and Cash are always on budget; Mortgage and the tracking asset types are always off budget.
