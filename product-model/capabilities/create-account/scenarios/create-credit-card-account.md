---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a Credit account with a name and the amount currently owed
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product creates the Account on budget and records the debt as an outflow Transaction in the Transfers category, outside every spending category
  kind: product
  actor: user
  entities:
  - {entity: account, effect: creates, to: Open, facts: [Name, Type, Currency, On budget, Balance]}
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Outflow, Memo, Category, Converted amount], with: account}
  - {entity: budget, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product adds a payment Category named after the card in the Credit Card Payments group, creating the group if needed
  kind: product
  actor: user
  entities:
  - {entity: category, effect: creates, facts: [Name, Group, Funding priority, Exclude from budget pace, Linked account]}
  - {entity: category-group, effect: reads, facts: [System group]}
  contexts:
    web:
      place: web-app::signed-in
---

# Create a credit card account

## Trigger

A person adds a credit card they already carry a balance on.

## Outcome

The card shows its debt, its payment category starts at zero, and Ready to Assign and categories are unchanged.
