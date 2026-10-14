---
appliesTo:
- {type: capability, id: undo-import}
- {type: capability, id: delete-import-entry}
- {type: entity, id: import-run}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/import/import-history-service.ts
---

# Undoing an import removes only what it created

An undo removes the transactions, accounts and categories that import created and nothing else; deleting a history entry removes only the entry.
