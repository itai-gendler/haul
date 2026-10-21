---
appliesTo:
- type: capability
  id: extract-archives
- type: entity
  id: archive
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#on_download_finished
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#extract_dir
---

# A package is extracted once all its downloads are finished

With Extract finished packages automatically on, extraction starts when the package's last download finishes and no part of its archives is still loading in the same folder. Extract is offered only once every download of the package is finished. Only complete archive sets are opened; a set with a missing part is named and left alone.
