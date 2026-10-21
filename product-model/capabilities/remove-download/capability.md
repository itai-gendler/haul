---
availability:
- place: haul-web::signed-in
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#delete
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#clear_finished
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#delete_download
- kind: code
  role: implementation
  target: ui/src/routes/Downloads.tsx#DownloadsPage
---

# Remove download

The user removes single links from the link grabber or downloads from the list. A running download stops and its partial data is deleted; a finished file stays on disk.
