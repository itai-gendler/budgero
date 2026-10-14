---
kind: edge
routes:
  web: Web
steps:
- text: The User enters a transaction in an account whose currency differs from the display currency
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: 'The Product resolves the exchange rate for the date: a custom rate for the period, then a fetched daily rate, then a manual rate, then the nearest earlier rate'
  kind: product
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Currency]}
  - {entity: budget, effect: reads, facts: [Display currency]}
  - {entity: custom-rate, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records the Transaction with the original amount, the rate and the converted amount
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Exchange rate]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Add a transaction in another currency

## Trigger

A person pays abroad or keeps an account in another currency.

## Outcome

The register shows the original amount and the budget sees the converted one.

## Edge cases

- A rate entered on the transaction overrides the resolved rate.
- With no fiat rate available the amount is converted 1:1, marked pending, and reconverted once a rate is known.
