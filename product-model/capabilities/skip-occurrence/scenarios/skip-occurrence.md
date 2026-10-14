---
kind: primary
routes:
  settings: Recurring Transactions page
  register: Account register upcoming panel
steps:
- text: The User chooses Skip on a scheduled occurrence
  kind: actor
  actor: user
  entities:
  - {entity: occurrence, effect: reads, facts: []}
  contexts:
    settings:
      place: web-app::signed-in::recurring-transactions
    register:
      place: web-app::signed-in::account
- text: The Product marks the Occurrence skipped; the series continues with the next date
  kind: product
  actor: user
  entities:
  - {entity: occurrence, effect: changes, from: Scheduled, to: Skipped, facts: []}
  contexts:
    settings:
      place: web-app::signed-in::recurring-transactions
    register:
      place: web-app::signed-in::account
---

# Skip an occurrence

## Trigger

A bill is waived this month.

## Outcome

The occurrence leaves the upcoming list and forecasts; the next one is untouched.
