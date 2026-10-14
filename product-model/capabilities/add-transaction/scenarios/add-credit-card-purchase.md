---
kind: primary
routes:
  web: Web
steps:
- text: The User enters a purchase on a credit card categorised to a spending category
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records the Transaction against the card
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product moves the budgeted part of the spending into the card's payment category
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: [Available, Linked account]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Add a credit card purchase

## Trigger

A person pays for groceries with a credit card.

## Outcome

Groceries shows the spending, and the card's payment category holds the money set aside to pay it.

## Edge cases

- Spending beyond what the category had available becomes card debt rather than payment money.
