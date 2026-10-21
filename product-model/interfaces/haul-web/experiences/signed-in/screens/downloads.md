---
entities:
- entity: package
  shows:
  - Name
  - Extraction error
- entity: download
  shows:
  - File name
  - Hoster
  - Size
  - Progress
  - Error
  - Next try
  - Checksum result
  - Subfolder
- entity: settings
  shows:
  - Parallel downloads
  - Connections per file
  - Bandwidth limit
  - Running downloads folder
  - Finished files folder
  - Extractors
- entity: account
  shows:
  - Premium
  - Traffic left
entryPoints:
- haul-web: /
references:
- kind: code
  role: implementation
  target: ui/src/routes/Downloads.tsx#DownloadsPage
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#stats
---

# Downloads

The started packages and their downloads with live progress, speed and time left, the total speed
against the bandwidth limit, active slots, the queue, what finished today, premium traffic and disk
space. A notice says when no extractor is installed.
