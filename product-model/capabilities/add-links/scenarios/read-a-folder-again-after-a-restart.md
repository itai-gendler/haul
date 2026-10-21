---
kind: edge
routes:
  web: Haul web
steps:
- text: Haul restarted while a folder link was still being read
  kind: condition
  unattended: true
  entities:
  - entity: download
    as: folder-link
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product reads the folder again and replaces the link with its files, keeping the package name and target
    folder as they are
  kind: product
  entities:
  - entity: download
    as: folder-link
    effect: removes
    from: Reading folder
  - entity: download
    as: file-link
    effect: creates
    to: In the link grabber
    facts:
    - Link
    - File name
    - Hoster
    - Online status
    - Size
    - Checksum
    - Subfolder
    - Download password
  - entity: package
    effect: reads
    facts:
    - Name
    - Target folder
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Read a folder again after a restart

## Trigger

The server restarts while a folder is being read.

## Outcome

The folder's files arrive as if the restart had not happened.
