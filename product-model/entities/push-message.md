---
domain: push-api
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/push_service.go
- kind: code
  role: implementation
  target: packages/app/src/shared/runtime/app-runtime.ts
  title: AppRuntime.processPushQueue
---

# Push message

One encrypted operation a push client sent, waiting in the workspace's push
queue until a member's app decrypts and applies it. The server can read only
its message id and status.

## Information kept

- **Message id** — the optional client-chosen id that deduplicates retries and later identifies the transaction it added
- **Received at** — when the server queued it
- **Operation** — the encrypted operation: add a transaction, update or delete one added earlier, add a transfer, or delete a transfer

## States

### Pending

Queued and not yet applied.

### Processed

Applied to the workspace by a member's app.

### Failed

Could not be decrypted, read or applied; its error is in the audit log.
