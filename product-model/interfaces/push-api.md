---
type: api
actors:
- push-client
entryPoints:
- api: /api/v1/push
references:
- kind: code
  role: implementation
  target: packages/server/internal/adapter/driving/http/handler/push.go
  title: PushMutation
- kind: code
  role: implementation
  target: packages/server/internal/adapter/driving/http/routes/routes.go
- kind: doc
  role: intent
  target: packages/website/content/docs/push-api.mdx
  title: Push API overview
- kind: doc
  role: context
  target: packages/sdk-python/README.md
  title: Python SDK
---

# Push API

The HTTPS endpoint other systems use to send end-to-end encrypted transaction
operations into a person's default workspace with a bearer token. The Python
SDK wraps it.
