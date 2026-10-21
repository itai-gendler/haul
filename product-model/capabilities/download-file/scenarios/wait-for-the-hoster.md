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
- text: The hoster asks for a wait, such as a free download limit or the time between two free downloads
  kind: condition
  entities:
  - entity: download
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product queues the download until the time the hoster named, without counting an attempt
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Connecting
    to: Waiting
    facts:
    - Next try
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Wait for the hoster

## Trigger

The user downloads for free from a hoster with limits.

## Outcome

The download waits and starts again when the hoster allows it, with all its retries left.
