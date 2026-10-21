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
  target: ui/src/routes/Accounts.tsx#AccountsPage
---

# Activate account

The user turns an account's Active switch on so downloads use it again.
