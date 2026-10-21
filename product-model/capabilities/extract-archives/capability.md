---
availability:
- place: haul-web::signed-in
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#on_download_finished
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#extract_package
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#extract_dir
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#extract_archive
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#extract_paths
- kind: doc
  role: intent
  target: docs/extraction.md
---

# Extract archives

Haul extracts a package's own archives into its folder once all its downloads are finished, and the user starts an extraction from the downloads or the Done view. Only complete archive sets are opened; the known passwords are tried before the user is asked.
