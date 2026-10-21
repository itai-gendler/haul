---
appliesTo:
- type: capability
  id: remove-download
- type: capability
  id: remove-package
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#delete
---

# Removing downloads never deletes finished files

Removing a download or a package from the list deletes partial data only; files already in the done folder stay. A package left without downloads disappears.
