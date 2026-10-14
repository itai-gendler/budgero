---
domain: recurring-transactions
relations:
- {entity: occurrence, verb: has, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/types.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/recurring-transactions.mdx
  title: Recurring transactions
---

# Recurring transaction

A template for money that moves on a rhythm, such as rent, salary or a
subscription. It reminds people of each due date and posts a real transaction
only when someone marks the occurrence ready.

## Information kept

- **Name** — what the template is called; also the default memo
- **Memo** — the memo given to posted transactions
- **Direction** — Bill (outflow) or Income (inflow); always an outflow from the source account for a transfer
- **Amount** — the amount each occurrence posts, in the source account's currency
- **Account** — the account it posts to, or transfers from
- **Transfer destination** — the account a transfer template moves money into
- **Category** — the category posted transactions get; the Transfers category for a transfer unless it crosses the budget boundary
- **Schedule** — the start date and cadence: daily, weekly, every 2 weeks, monthly, every 2 months, quarterly, every 6 months, yearly or a custom interval
- **Ends** — never, on a date, or after a number of occurrences counted from the first, posted and skipped ones included
- **Reminder days** — how many days before a due date to remind; 0 reminds on the due date

## States

### Active

Generating occurrences and reminders.

### Paused

No reminders, and its occurrences cannot be posted until it is resumed.
