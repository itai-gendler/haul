---
appliesTo:
- type: entity
  id: download
  effect: changes
permits:
- actors:
  - user
- unattended: true
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#require_auth
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#execute
---

# Only the user, or Haul on its own, changes a download

Starting, pausing, resuming and answering questions for downloads needs the login or the API token; the queue moves downloads on its own.
