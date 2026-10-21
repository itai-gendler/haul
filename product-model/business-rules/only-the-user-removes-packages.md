---
appliesTo:
- type: entity
  id: package
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
  target: crates/haul/src/engine/mod.rs#delete
---

# Only the user, or Haul on its own, removes a package

Discarding or removing packages needs the login; a package left without downloads disappears, also when Haul removes extracted downloads from the list.
