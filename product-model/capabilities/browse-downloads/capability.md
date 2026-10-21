---
availability:
- place: haul-web::signed-in
domain: downloads
references:
- kind: code
  role: implementation
  target: ui/src/routes/Downloads.tsx#DownloadsPage
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#list_packages
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#stats
- kind: code
  role: implementation
  target: crates/haul/src/events.rs
- kind: code
  role: implementation
  target: ui/src/components/status.ts#describe
---

# Browse downloads

The user follows the started packages and their downloads live: progress, speed, time left, why something waits or failed, and totals for slots, queue, today, premium traffic and disk space.
