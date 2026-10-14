---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a Loan account with the original debt and what has been paid so far
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product creates the Account and records the original debt as an outflow Transaction and the payments so far as an inflow Transaction, both in the Transfers category
  kind: product
  actor: user
  entities:
  - {entity: account, effect: creates, to: Open, facts: [Name, Type, Currency, On budget, Balance, Original debt, Paid so far]}
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Memo, Category, Converted amount], with: account}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product adds a linked Category named after the loan in the Liabilities group
  kind: product
  actor: user
  entities:
  - {entity: category, effect: creates, facts: [Name, Group, Funding priority, Exclude from budget pace, Linked account]}
  - {entity: category-group, effect: reads, facts: [System group]}
  contexts:
    web:
      place: web-app::signed-in
---

# Create a loan account

## Trigger

A person starts budgeting payments on a car loan.

## Outcome

The loan shows what is still owed and its linked category is ready to be funded each month.

## Edge cases

- A mortgage gets the same linked category and starts off budget.
