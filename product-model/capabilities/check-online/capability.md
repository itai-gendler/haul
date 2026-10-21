---
availability:
- place: haul-web::signed-in
domain: link-grabber
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#check_package
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#check_download
- kind: code
  role: implementation
  target: ui/src/routes/Collector.tsx#CollectedPackage
---

# Check online

The user asks Haul to check every link of a package in the link grabber again: hoster links through their plugin, without an account, and direct links with a short request.
