---
appliesTo:
- type: capability
  id: move-items
- type: capability
  id: delete-items
- type: capability
  id: delete-archives
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#extracting_near
---

# A folder being extracted is not moved or deleted

While an extraction runs in a folder, in a folder inside it or in a folder around it, moving, deleting and deleting archives there are refused.
