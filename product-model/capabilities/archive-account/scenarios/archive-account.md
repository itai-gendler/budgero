---
kind: primary
routes:
  web: Web
steps:
- text: The User archives an account
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product archives the Account
  kind: product
  actor: user
  entities:
  - {entity: account, effect: changes, from: Open, to: Archived, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: Its transactions stay in history and reports, and its payment or linked category may now be deleted
  kind: condition
  entities:
  - {entity: transaction, effect: reads, facts: [Date]}
  - {entity: category, effect: reads, facts: [Linked account]}
  - {entity: report, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Archive an account

## Trigger

A person closed the account at their bank.

## Outcome

The account is hidden from pickers and lists, with every transaction still in history.

## Edge cases

- A remaining balance keeps counting toward net worth and, on budget, toward Ready to Assign; bringing it to zero first is advised.
