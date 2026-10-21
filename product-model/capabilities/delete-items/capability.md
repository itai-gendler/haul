---
availability:
- place: haul-web::signed-in
domain: done
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#delete_files
- kind: code
  role: implementation
  target: crates/haul/src/files.rs#delete
- kind: code
  role: implementation
  target: ui/src/routes/Done.tsx#DonePage
---

# Delete items

The user deletes selected files and folders from the done folder for good, after confirming.
