---
domain: done
relations:
- entity: file
  verb: contains
  cardinality: one-to-many
- entity: archive
  verb: contains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: crates/haul/src/files.rs#list
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#list_files
- kind: code
  role: implementation
  target: ui/src/routes/Done.tsx#folderState
- kind: doc
  role: intent
  target: docs/extraction.md#the-done-view
---

# Folder on disk

A folder in the done folder, usually a package's target folder, shown as it is on disk.

## Information kept

- **Name** — the folder's name
- **Path** — where it is below the done folder
- **Size** — the size of everything in it
- **Modified** — when it last changed
- **Archive files** — how many archive files are directly inside
- **State** — extracted, archives left, not extracted, extraction failed, finished, or not from Haul
