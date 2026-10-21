---
kind: edge
routes:
  web: Haul web
steps:
- text: A package finishes while a part of its archive still loads in another package of the same folder
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts:
    - File name
  - entity: package
    effect: reads
    facts:
    - Target folder
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product does not start the extraction; the other package's last download starts it
  kind: product
  entities:
  - entity: package
    effect: reads
    facts:
    - Target folder
  - entity: download
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Wait for a part in another package

## Trigger

A package was started in parts, or two packages share a folder.

## Outcome

The archive is extracted once, when its last part arrives.
