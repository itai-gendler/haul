---
appliesTo:
- type: capability
  id: download-file
- type: capability
  id: move-items
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#unique_path
- kind: code
  role: implementation
  target: crates/haul/src/files.rs#free_name
---

# A finished file never overwrites another

A finished file whose name is taken in its folder gets a number added; moving items in the Done view does the same.
