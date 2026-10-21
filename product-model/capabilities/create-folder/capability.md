---
availability:
- place: haul-web::signed-in
domain: done
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#make_folder
- kind: code
  role: implementation
  target: crates/haul/src/files.rs#valid_name
- kind: code
  role: implementation
  target: ui/src/routes/Done.tsx#NewFolderDialog
---

# Create folder

The user creates a new folder in the folder open in the Done view.
