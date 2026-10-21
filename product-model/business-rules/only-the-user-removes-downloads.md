---
appliesTo:
- type: entity
  id: download
  effect: removes
permits:
- actors:
  - user
- unattended: true
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#require_auth
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#replace_link
---

# Only the user, or Haul on its own, removes a download

Removing downloads needs the login; Haul itself replaces a folder link with its files.
