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
    as: limited
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
    as: limited
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
- text: The hoster limits everything from this server, for example an IP block or taken free slots
  kind: condition
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product queues the download until the time the hoster named, without counting an attempt
  kind: product
  entities:
  - entity: download
    as: limited
    effect: changes
    from: Connecting
    to: Waiting
    facts:
    - Next try
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product holds every other waiting download of that hoster until then, with the hoster's message, also
    those queued later
  kind: product
  entities:
  - entity: download
    as: others
    effect: changes
    facts:
    - Next try
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Hold every download of a limited hoster

## Trigger

A hoster says the limit applies to everything from this address.

## Outcome

No download of that hoster runs into the limit again; the others go on.
