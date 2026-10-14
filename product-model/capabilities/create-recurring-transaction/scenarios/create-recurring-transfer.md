---
kind: primary
routes:
  web: Web
steps:
- text: The User creates a recurring Transfer with a source and a destination account
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The Product saves it as an outflow from the source in the Transfers category, keeping a chosen category only when the transfer crosses the budget boundary, and generates its Occurrences
  kind: product
  actor: user
  entities:
  - {entity: recurring-transaction, effect: creates, to: Active, facts: [Name, Memo, Direction, Amount, Account, Category, Schedule, Ends, Reminder days, Transfer destination]}
  - {entity: occurrence, effect: creates, to: Scheduled, facts: [Due date], with: recurring-transaction}
  - {entity: budget, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
---

# Create a recurring transfer

## Trigger

A person moves money to savings on every payday.

## Outcome

Each occurrence will post two linked legs when marked ready.
