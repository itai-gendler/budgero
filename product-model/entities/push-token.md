---
domain: push-api
references:
- kind: code
  role: implementation
  target: packages/server/internal/adapter/driving/http/handler/push.go
- kind: code
  role: implementation
  target: packages/server/internal/application/push_token.go
---

# Push API token

The bearer token a person generates for the Push API. It sends operations
into the person's default workspace; the server keeps only its hash.

## Information kept

- **Enabled** — whether the token is accepted
- **Created at** — when it was generated
- **Last used** — when a push last used it
- **Workspace** — the person's default workspace, which pushed operations go into
