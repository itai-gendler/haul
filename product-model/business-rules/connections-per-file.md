---
appliesTo:
- type: capability
  id: download-file
- type: capability
  id: change-download-settings
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#plan_segments
- kind: code
  role: implementation
  target: crates/haul/src/engine/limiter.rs
---

# A file loads over at most Connections per file connections

A download with a known size splits into parts of at least 4 MiB, as many as Connections per file and the hoster plugin allow; without range support it loads over one. All downloads together stay under the Bandwidth limit.
