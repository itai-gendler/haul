---
availability:
- place: haul-web::signed-in
domain: accounts-and-plugins
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#update_account
- kind: code
  role: implementation
  target: ui/src/routes/Accounts.tsx#EditSecret
---

# Change account login

The user replaces an account's password, key or cookies. Haul drops the old hoster session and checks the account again.
