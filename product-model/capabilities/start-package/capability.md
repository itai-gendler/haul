---
availability:
- place: haul-web::signed-in
domain: link-grabber
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#start_package
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#start_selected
- kind: code
  role: implementation
  target: ui/src/routes/Collector.tsx#startPackage
- kind: code
  role: implementation
  target: ui/src/routes/Collector.tsx#CollectorPage
---

# Start package

The user starts a package from the link grabber: its checked links that are not offline go into the queue. Starting only some files moves them into a package of their own.
