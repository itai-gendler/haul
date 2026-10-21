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
- text: The network fails or the hoster is busy
  kind: condition
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product counts the attempt and puts the download back in the queue for 10 seconds, doubling with each
    attempt up to 10 minutes
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Connecting
    to: Waiting
    facts:
    - Attempts
    - Next try
    - Error
  - entity: settings
    effect: reads
    facts:
    - Retries
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Try again after a failed attempt

## Trigger

An attempt fails for a reason that may pass.

## Outcome

The download shows Retrying in with the reason and starts again on its own.
