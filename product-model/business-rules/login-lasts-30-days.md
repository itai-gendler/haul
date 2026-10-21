---
appliesTo:
- type: capability
  id: log-in
- type: capability
  id: create-login
- type: capability
  id: log-out
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#new_session
---

# A login lasts 30 days in its browser

Logging in or creating the login signs that browser in for 30 days or until it logs out; the downloads run on whether anyone is signed in or not.
