---
kind: primary
routes:
  settings: Recurring Transactions page
  register: Account register upcoming panel
steps:
- text: The User chooses Mark ready on a scheduled occurrence
  kind: actor
  actor: user
  entities:
  - {entity: occurrence, effect: reads, facts: []}
  contexts:
    settings:
      place: web-app::signed-in::recurring-transactions
    register:
      place: web-app::signed-in::account
- text: The Product records an uncleared Transaction from the template, dated on the due date
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount]}
  - {entity: recurring-transaction, effect: reads, facts: [Amount, Account, Category, Memo, Name]}
  contexts:
    settings:
      place: web-app::signed-in::recurring-transactions
    register:
      place: web-app::signed-in::account
- text: The Product marks the Occurrence ready and generates the next ones
  kind: product
  actor: user
  entities:
  - {entity: occurrence, effect: changes, from: Scheduled, to: Ready, facts: []}
  contexts:
    settings:
      place: web-app::signed-in::recurring-transactions
    register:
      place: web-app::signed-in::account
- text: The Product runs the budget's enabled continuous rules on the posted transaction
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: [Payee, Memo, Category]}
  - {entity: rule, effect: reads, facts: []}
  - {entity: budget, effect: reads, facts: []}
  contexts:
    settings:
      place: web-app::signed-in::recurring-transactions
    register:
      place: web-app::signed-in::account
---

# Post a recurring occurrence

## Trigger

The rent is due and a person confirms it is paid.

## Outcome

The register holds the real transaction and the occurrence is no longer upcoming.

## Edge cases

- Confirming a few days early still dates the transaction on the due date.
