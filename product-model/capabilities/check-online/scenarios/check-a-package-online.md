---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Check online on a package
  kind: actor
  actor: user
  entities:
  - entity: package
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product asks each link's hoster plugin, as a guest, whether the file is there, and asks the server of
    each direct link for its first byte
  kind: product
  actor: user
  entities:
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
  - entity: download
    effect: changes
    facts:
    - Online status
    - File name
    - Size
    - Checksum
    - Error
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: Each link shows Online with its name and size
  kind: condition
  entities:
  - entity: download
    effect: reads
    facts:
    - Online status
    - File name
    - Size
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Check a package online

## Trigger

The user wants to know whether the files are still there before starting.

## Outcome

The links show Online, with the names and sizes the hosters report.
