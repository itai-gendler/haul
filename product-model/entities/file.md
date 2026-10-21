---
domain: done
references:
- kind: code
  role: implementation
  target: crates/haul/src/files.rs#list
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#unique_path
---

# File on disk

A file in the done folder: a finished download, an extracted file or anything else put there.

## Information kept

- **Name** — the file's name
- **Path** — where it is below the done folder
- **Size** — its size
- **Modified** — when it last changed
