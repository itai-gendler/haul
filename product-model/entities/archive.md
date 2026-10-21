---
domain: done
relations:
- entity: file
  verb: consists of
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#find_archives
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#archive_set
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#missing_volumes
- kind: doc
  role: intent
  target: docs/extraction.md#what-is-extracted
---

# Archive set

A RAR, 7z or ZIP archive in the done folder: one file, or a set of numbered parts that open together.

## Information kept

- **Name** — the archive's name without part number and type
- **Parts** — the files that make up the set
- **Missing parts** — parts missing from the numbering, or the next part the last one announces
