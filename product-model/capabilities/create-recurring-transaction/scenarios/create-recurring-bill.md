---
kind: primary
routes:
  web: Web
steps:
- text: The User creates a Bill with name, amount, account, category, schedule, end and reminder days
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The Product saves the active Recurring transaction and generates its Occurrences up to about six months ahead
  kind: product
  actor: user
  entities:
  - {entity: recurring-transaction, effect: creates, to: Active, facts: [Name, Memo, Direction, Amount, Account, Category, Schedule, Ends, Reminder days]}
  - {entity: occurrence, effect: creates, to: Scheduled, facts: [Due date], with: recurring-transaction}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
---

# Create a recurring bill

## Trigger

A person wants to be reminded of rent every month.

## Outcome

The template lists its upcoming due dates; nothing is posted yet.

## Edge cases

- An end after a number of occurrences counts from the first occurrence, including posted and skipped ones.
