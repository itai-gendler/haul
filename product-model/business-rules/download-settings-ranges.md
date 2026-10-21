---
appliesTo:
- type: capability
  id: change-download-settings
- type: entity
  id: settings
  facts:
  - Parallel downloads
  - Connections per file
  - Retries
references:
- kind: code
  role: implementation
  target: crates/haul/src/db.rs#Settings
---

# Download settings stay within their ranges

Parallel downloads lies between 1 and 20, Connections per file between 1 and 16, and Retries at most 50; values outside are brought into range when saved.
