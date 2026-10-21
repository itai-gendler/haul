---
appliesTo:
- type: entity
  id: package
  effect: changes
permits:
- actors:
  - user
- unattended: true
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#require_auth
---

# Only the user, or Haul on its own, changes a package

Renaming, starting and extracting packages needs the login or the API token; Haul's own queue and extraction change packages on their own. Link sites can only add new packages to the link grabber.
