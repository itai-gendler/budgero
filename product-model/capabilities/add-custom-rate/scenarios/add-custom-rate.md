---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Add Exchange Rate and enters the pair, the rate and a start date with an optional end date
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::currencies
- text: The Product saves the Custom rate and recalculates the converted amounts of transactions in that range
  kind: product
  actor: user
  entities:
  - {entity: custom-rate, effect: creates, facts: [From currency, To currency, Rate, Start date, End date]}
  - {entity: transaction, effect: changes, facts: [Exchange rate, Converted amount]}
  contexts:
    web:
      place: web-app::signed-in::currencies
---

# Add a custom rate

## Trigger

A person exchanged money at a known rate for a trip.

## Outcome

The trip's transactions convert at that rate.

## Edge cases

- Transactions with a rate entered on the transaction itself keep that rate.
