---
availability:
- place: haul-web::signed-in
domain: link-grabber
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#update_package
- kind: code
  role: implementation
  target: ui/src/routes/Collector.tsx#CollectedPackage
---

# Edit package

In the link grabber the user renames a package and changes the folder inside the done folder its files go to; each field is saved when the user leaves it.
