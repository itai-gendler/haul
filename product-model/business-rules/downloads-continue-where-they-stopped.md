---
appliesTo:
- type: capability
  id: download-file
- type: capability
  id: pause-download
- type: capability
  id: resume-download
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#persist_segments
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#new
---

# Downloads continue where they stopped

A paused download, or one cut off by a restart, keeps its loaded bytes and continues from them when its turn comes.
