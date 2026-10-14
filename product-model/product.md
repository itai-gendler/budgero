---
id: budgero
summary: 'Local-first, end-to-end encrypted zero-based budgeting: give every unit of income a job through monthly category assignments, goals, rollover, split and recurring transactions, shared with a household.'
category: personal-finance
tags:
- budgeting
- zero-based-budgeting
- personal-finance
- local-first
- end-to-end-encryption
authors:
- name: tombadilo-bombadilo
  url: https://github.com/tombadilo-bombadilo
license: AGPL-3.0-only
languages:
- en
- de
- fr
- es
- nl
limitations:
- Budget data is encrypted on the device; the server keeps only ciphertext and wrapped keys, so data behind a forgotten master password cannot be recovered.
- Recurring transactions never post themselves; every occurrence waits for someone to mark it ready.
- A person who owns workspaces has at most five collaborator seats across all of them, counting members and pending invitations.
- A budget is kept in one fiat display currency; cryptocurrencies are allowed only as account currencies.
- Categories are deleted, never archived; accounts are archived, or deleted once they hold no transactions.
references:
- kind: doc
  role: context
  target: README.md
  title: Repository README
- kind: doc
  role: intent
  target: packages/website/content/docs/zero-based-budgeting.mdx
  title: Zero-Based Budgeting with Budgero
- kind: doc
  role: context
  target: packages/website/content/docs/security.mdx
  title: Security model
---

# Budgero

Budgero is a personal budgeting application built around zero-based budgeting.
People record the accounts where their money lives and every transaction that
moves it, then give each unit of income a job by assigning it to categories
month by month. Ready to Assign shows the money that still has no job,
category balances roll over from month to month, goals compute what each
category needs, and recurring transactions remind people of bills before they
are due. Budgets live in workspaces that a household can share; the data is
kept on each device and synchronised end-to-end encrypted.

## Intent

Zero-based budgeting gives every unit of income a job the moment it enters the
system: instead of letting cash drift in a general balance, people decide
upfront which expenses, goals and buffers it should cover, and reassign money
when reality changes. Budgero is designed around that method so day-to-day work
mirrors it, while staying local-first and zero-knowledge: the data lives on the
device and the server can never read it. It ships as the hosted Budgero Cloud
and as a free self-hosted edition built from the same source.
