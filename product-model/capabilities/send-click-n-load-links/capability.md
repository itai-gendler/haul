---
availability:
- place: click-n-load
references:
- kind: code
  role: implementation
  target: crates/haul/src/cnl.rs#flash_add
- kind: code
  role: implementation
  target: crates/haul/src/cnl.rs#flash_addcrypted2
- kind: code
  role: implementation
  target: crates/haul/src/cnl.rs#submit
- kind: code
  role: implementation
  target: crates/haul/src/cnl.rs#decrypt_cnl2
- kind: code
  role: implementation
  target: extension/src/cnl-page.ts
- kind: doc
  role: intent
  target: docs/click-n-load.md
---

# Send Click'n'Load links

A link site sends links to Click'n'Load, plain or encrypted, with a package name and passwords. Haul puts them in a new package in the link grabber; they never start on their own.
