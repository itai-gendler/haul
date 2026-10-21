---
appliesTo:
- type: capability
  id: download-file
- type: capability
  id: change-download-settings
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#fill_slots
---

# Downloads start in package order, up to Parallel downloads

The queue starts waiting downloads in the order their packages were added, as many at a time as Parallel downloads allows, and skips those whose next try lies ahead.
