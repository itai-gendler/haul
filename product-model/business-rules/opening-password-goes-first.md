---
appliesTo:
- type: entity
  id: settings
  facts:
  - Archive passwords
- type: capability
  id: extract-archives
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#remember_archive_password
---

# The password that opened an archive goes to the top of the list

Whichever password opened an archive, from any source, is kept first in the archive passwords and tried first next time.
