---
appliesTo:
- type: capability
  id: extract-archives
- type: capability
  id: enter-archive-password
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#candidates
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#extract_archive
---

# Archive passwords are tried in a fixed order

An archive is tried with no password, then the package's passwords, then its own name, then the archive passwords, and only then is the user asked, at most three times and only while Ask for the archive password when none fits is on.
