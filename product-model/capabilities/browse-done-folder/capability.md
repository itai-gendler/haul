---
availability:
- place: haul-web::signed-in
domain: done
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#list_files
- kind: code
  role: implementation
  target: ui/src/routes/Done.tsx#DonePage
- kind: code
  role: implementation
  target: ui/src/routes/Done.tsx#folderState
---

# Browse done folder

The user browses the done folder as it is on disk, folder by folder, with each folder's state as Haul sees it.
