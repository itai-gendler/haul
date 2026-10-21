---
availability:
- place: haul-web::signed-in
domain: done
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#move_files
- kind: code
  role: implementation
  target: crates/haul/src/files.rs#move_within
- kind: code
  role: implementation
  target: ui/src/routes/Done.tsx#MoveDialog
---

# Move items

The user moves selected files and folders to another folder of the done folder, optionally a new one.
