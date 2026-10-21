---
appliesTo:
- type: capability
  id: add-links
- type: capability
  id: edit-package
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#rename_after_crawl
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#crawl_package
---

# A folder link names its package unless the user did

When a folder link is read, the package takes the folder's name and target folder, unless the user named them when adding or changed them meanwhile. The folder's password goes to each of its files.
