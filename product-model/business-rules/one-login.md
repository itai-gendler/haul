---
appliesTo:
- type: capability
  id: create-login
- type: capability
  id: log-in
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#setup
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#ensure_initial_user
---

# Haul has exactly one login

The login is created once, on the first visit or from the first start's configuration; afterwards the page only asks to log in. There are no other users and no roles.
