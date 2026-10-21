---
kind: edge
routes:
  web: Haul web
steps:
- text: A queued download reaches the front of the queue
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts:
    - Next try
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product has the link's hoster plugin get the direct address
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Waiting
    to: Connecting
    facts: []
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The hoster or the link's server says the file is gone
  kind: condition
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product marks the download failed and the file offline
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Connecting
    to: Failed
    facts:
    - Online status
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Find the file offline

## Trigger

The file was deleted at the hoster.

## Outcome

The download shows the hoster's message under Failed and is not tried again.
