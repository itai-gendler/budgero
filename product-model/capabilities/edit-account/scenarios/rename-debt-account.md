---
kind: primary
routes:
  web: Web
steps:
- text: The User renames a credit card account
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product saves the Account and renames its payment Category to match
  kind: product
  actor: user
  entities:
  - {entity: account, effect: changes, facts: [Name]}
  - {entity: category, effect: changes, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product updates the memos of Transfer legs that mention the old name
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: changes, facts: [Memo]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Rename a credit card or loan

## Trigger

A person renames a card or loan.

## Outcome

The account, its category and its transfer memos all carry the new name.
