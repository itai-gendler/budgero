---
domain: workspaces-and-sharing
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/invite.go
- kind: code
  role: implementation
  target: packages/server/internal/adapter/driving/http/handler/budget_spaces.go
---

# Invitation

A one-time invite link a workspace owner creates for someone to join. The link
carries a secret in its fragment, which never reaches the server; the server
keeps only a hash of it and the workspace key wrapped under it.

## Information kept

- **Invitee email** — the optional address the invitation is meant for
- **Expires at** — when the link stops working; seven days after creation by default
- **Invite link** — the link, carrying the one-time secret, that the invitee opens or pastes as an invite code

## States

### Pending

Created and not yet used; it occupies a collaborator seat.

### Redeemed

Used once by the person who joined with it.

### Expired

Someone tried to use it after it expired.
