---
entities:
- {entity: recurring-transaction, shows: [Name, Direction, Amount, Account, Category, Schedule, Ends, Reminder days], collects: [Name, Memo, Direction, Amount, Account, Transfer destination, Category, Schedule, Ends, Reminder days]}
- {entity: occurrence, shows: [Due date]}
- {entity: category, shows: [Name]}
- {entity: account, shows: [Name]}
entryPoints:
- web-app: /settings/recurring
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/RecurringTransactionsPage.tsx
---

# Recurring transactions

Every recurring transaction of the budget with its schedule and upcoming occurrences, and the device notification switch.
