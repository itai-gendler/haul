---
availability:
- place: haul-web::signed-in
domain: accounts-and-plugins
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#create_account
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#run_account_check
- kind: code
  role: implementation
  target: ui/src/routes/Accounts.tsx#AddAccount
- kind: doc
  role: intent
  target: docs/hosters.md#accounts
---

# Add account

The user adds a hoster account with the fields that hoster's plugin asks for. Haul stores the password encrypted and checks the account right away.
