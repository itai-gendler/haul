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
- text: The attempt fails and the download has used up Retries
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Retries
  - entity: download
    effect: reads
    facts:
    - Attempts
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product marks the download failed, naming the reason and the number of attempts
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Connecting
    to: Failed
    facts:
    - Attempts
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Run out of retries

## Trigger

A hoster keeps failing.

## Outcome

The download shows the error under Failed until the user resumes or removes it.
