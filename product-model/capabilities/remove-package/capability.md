---
availability:
- place: haul-web::signed-in
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#delete_package
- kind: code
  role: implementation
  target: ui/src/routes/Collector.tsx#CollectedPackage
- kind: code
  role: implementation
  target: ui/src/routes/Downloads.tsx#PackageRow
---

# Remove package

The user discards a package from the link grabber or removes a started one from the downloads, with all its links. Partial data is deleted; finished files stay on disk.
