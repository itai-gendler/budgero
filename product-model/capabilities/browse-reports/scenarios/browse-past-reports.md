---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a prebuilt view such as Spending, Flow or Wealth and picks a date range and accounts
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::reports
- text: The Product shows the report from the Transactions in range
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: [Date, Inflow, Outflow, Category]}
  - {entity: report, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::reports
---

# Read reports for a past period

## Trigger

A person reviews last quarter's spending.

## Outcome

The report reflects recorded transactions.
