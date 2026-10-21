---
appliesTo:
- type: capability
  id: browse-done-folder
- type: capability
  id: move-items
- type: capability
  id: create-folder
- type: capability
  id: delete-archives
- type: capability
  id: delete-items
- type: capability-scenario
  id: extract-from-the-done-view
references:
- kind: code
  role: implementation
  target: crates/haul/src/files.rs#resolve
- kind: code
  role: implementation
  target: crates/haul/src/files.rs#resolve_entry
---

# The Done view works only inside the done folder

Every path the Done view browses, extracts, moves, creates or deletes lies inside the done folder; the done folder itself cannot be moved or deleted.
