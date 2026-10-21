---
entities:
- entity: folder
  shows:
  - Name
  - Path
  - Size
  - Modified
  - Archive files
  - State
  collects:
  - Name
- entity: file
  shows:
  - Name
  - Size
  - Modified
- entity: archive
  shows:
  - Name
- entity: package
  shows:
  - Extraction error
entryPoints:
- haul-web: /fertig
references:
- kind: code
  role: implementation
  target: ui/src/routes/Done.tsx#DonePage
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#list_files
---

# Done

The done folder as it is on disk, one folder at a time, with each folder's state from Haul's point of
view, its size and free disk space; entries are selected with checkboxes.
