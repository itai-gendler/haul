---
availability:
- place: haul-web::signed-in
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#set_archive_passwords
- kind: code
  role: implementation
  target: ui/src/routes/Settings.tsx#ArchivePasswords
---

# Change archive passwords

The user edits the archive passwords under Settings → Archive passwords, one per line.
