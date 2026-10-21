---
availability:
- place: haul-web::signed-in
domain: done
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#delete_archives
- kind: code
  role: implementation
  target: ui/src/routes/Done.tsx#DonePage
---

# Delete archives

The user deletes every archive file in the selected folders, keeping their extracted contents.
