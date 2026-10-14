---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Download SQLite Database
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::data-management
- text: The Product downloads the decrypted workspace database and records when the last backup was made
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::data-management
---

# Export a database backup

## Trigger

A person keeps regular backups or moves to self-hosting.

## Outcome

A complete backup file is on the device.
