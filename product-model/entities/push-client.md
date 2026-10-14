---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: packages/sdk-python/src/budgero/client.py
- kind: doc
  role: intent
  target: packages/website/content/docs/push-api.mdx
  title: Push API overview
---

# Push client

An integration that sends transactions into Budgero through the Push API on a
person's behalf, such as the Python SDK or a script that reads bank emails. It
holds the person's Push API token and their workspace encryption key, and
encrypts every operation before sending it.
