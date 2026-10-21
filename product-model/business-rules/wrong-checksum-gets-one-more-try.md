---
appliesTo:
- type: capability
  id: download-file
- type: entity
  id: download
  facts:
  - Checksum result
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#execute
- kind: code
  role: implementation
  target: crates/haul/src/engine/hash.rs#verify
---

# A wrong checksum gets one more download

When a finished file does not match the checksum its hoster published, it is loaded once more from scratch; a second mismatch fails the download with checksum wrong. One checksum check runs at a time.
