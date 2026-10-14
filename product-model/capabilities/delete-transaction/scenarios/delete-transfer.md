---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes one leg of a transfer
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product removes both linked legs and corrects both accounts
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: deleted-leg, effect: removes, from: Uncleared}
  - {entity: transaction, as: partner-leg, effect: removes, from: Uncleared}
  - {entity: account, effect: reads, facts: [Balance]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Delete a transfer

## Trigger

A person removes a transfer entered by mistake.

## Outcome

Neither account shows the transfer any more.
