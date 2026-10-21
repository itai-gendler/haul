---
appliesTo:
- type: capability
  id: extract-archives
- type: entity
  id: archive
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#package_sets
---

# A package extracts only the archives it downloaded

Archives another package downloaded into the same folder are left to that package, so packages that share a folder do not get in each other's way.
