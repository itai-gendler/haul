---
availability:
- place: haul-web::signed-in
domain: accounts-and-plugins
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#delete_account
---

# Delete account

The user deletes a hoster account together with its saved hoster session.
