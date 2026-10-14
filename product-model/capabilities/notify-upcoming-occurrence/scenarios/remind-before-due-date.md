---
kind: edge
routes:
  web: Web
steps:
- text: An active template's scheduled occurrence reaches its reminder day and has not been notified
  kind: condition
  unattended: true
  entities:
  - {entity: occurrence, effect: reads, facts: [Due date, Notified at]}
  - {entity: recurring-transaction, effect: reads, facts: [Reminder days, Name, Amount]}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product shows a device notification for the upcoming bill or income and records that the Occurrence was notified
  kind: product
  entities:
  - {entity: occurrence, effect: changes, facts: [Notified at]}
  contexts:
    web:
      place: web-app::signed-in
---

# Remind before a due date

## Trigger

The app is open on a device that allowed notifications and a due date is near.

## Outcome

The person is reminded once per occurrence; the server never learns about the bill.
