---
availability:
- place: haul-web::signed-in
domain: accounts-and-plugins
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#check_account
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#run_account_check
---

# Check account

The user has Haul log in to the hoster again to refresh an account's state, type, expiry and traffic.
