---
availability:
- place: haul-web::signed-in
domain: downloads
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#pause
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#pause_all
- kind: code
  role: implementation
  target: ui/src/routes/Downloads.tsx#DownloadsPage
---

# Pause download

The user pauses one download, a package or everything that is waiting, connecting or downloading. Loaded bytes are kept.
