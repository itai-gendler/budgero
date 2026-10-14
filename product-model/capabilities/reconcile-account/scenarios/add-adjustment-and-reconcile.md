---
kind: edge
routes:
  web: Web
steps:
- text: The User chooses Reconcile and enters a bank balance that differs from the cleared balance
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records a cleared adjustment Transaction for the difference in the Income category
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: adjustment, effect: creates, to: Cleared, facts: [Date, Inflow, Outflow, Memo, Category, Converted amount]}
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product locks the cleared Transactions, the adjustment included, as reconciled and stamps the Account
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: adjustment, effect: changes, from: Cleared, to: Reconciled, facts: []}
  - {entity: transaction, as: cleared-transactions, effect: changes, from: Cleared, to: Reconciled, facts: []}
  - {entity: account, effect: changes, facts: [Reconciled at]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Reconcile with an adjustment

## Trigger

A small discrepancy is not worth hunting down.

## Outcome

The cleared balance matches the bank; on an on-budget account the adjustment moves Ready to Assign until it is recategorised.
