---
appliesTo:
- type: capability
  id: download-file
- type: capability
  id: activate-account
- type: capability
  id: deactivate-account
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#pick_account
- kind: code
  role: implementation
  target: crates/haul/src/plugins/mod.rs#Session
---

# The active account with the most traffic left is used

Of a hoster's accounts Haul uses an active one the hoster has not rejected, the one with the most traffic left first. Accounts that are turned off or Invalid are skipped. Calls with one account run one after the other.
