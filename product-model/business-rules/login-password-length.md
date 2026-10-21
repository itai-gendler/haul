---
appliesTo:
- type: capability
  id: create-login
- type: capability
  id: change-password
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#setup
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#change_password
---

# A login password has at least 8 characters

Creating the login and changing its password both refuse shorter passwords.
