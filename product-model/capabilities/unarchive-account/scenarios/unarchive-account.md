---
kind: primary
routes:
  web: Web
steps:
- text: The User unarchives an account
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product reopens the Account
  kind: product
  actor: user
  entities:
  - {entity: account, effect: changes, from: Archived, to: Open, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product relinks the card's payment Category or the loan's linked Category, recreating it if it was deleted
  kind: product
  actor: user
  entities:
  - {entity: category, effect: changes, facts: [Linked account]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Unarchive an account

## Trigger

A person starts using an old account again.

## Outcome

The account returns exactly as it was, with its payment mechanics working again.
