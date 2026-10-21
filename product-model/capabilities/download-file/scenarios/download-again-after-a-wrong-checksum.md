---
kind: edge
routes:
  web: Haul web
steps:
- text: The finished bytes do not match the checksum the hoster published
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts:
    - Checksum
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product drops the bytes and queues the download to load from scratch
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Downloading
    to: Waiting
    facts:
    - Checksum result
    - Progress
    - Attempts
    - Next try
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: When its turn comes, the Product gets the address again
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Waiting
    to: Connecting
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product loads every byte again
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Connecting
    to: Downloading
    facts:
    - Progress
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The second copy does not match either; the Product marks the download failed with checksum wrong
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Downloading
    to: Failed
    facts:
    - Checksum result
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Download again after a wrong checksum

## Trigger

A file arrives damaged.

## Outcome

After one more try the download shows checksum wrong; a matching second copy finishes normally.
