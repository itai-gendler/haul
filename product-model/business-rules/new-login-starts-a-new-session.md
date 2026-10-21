---
appliesTo:
- type: capability
  id: change-account-login
- type: entity
  id: account
  facts:
  - Hoster session
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#update_account
---

# A changed account login starts a new hoster session

Changing an account's user or password drops the saved hoster session and checks the account again.
