---
appliesTo:
- type: capability-scenario
  id: fail-without-an-account
- type: entity
  id: hoster-plugin
  facts:
  - Needs an account
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#execute
---

# A premium-only hoster is not tried without an account

A download of a hoster whose plugin needs an account fails at once when no usable account exists.
