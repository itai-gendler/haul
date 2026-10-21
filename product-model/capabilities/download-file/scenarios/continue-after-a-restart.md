---
kind: edge
routes:
  web: Haul web
steps:
- text: Haul stops while downloads are loading
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts:
    - Progress
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: At the next start, the Product puts every download that was connecting or loading back in the queue
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Downloading
    to: Waiting
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: When its turn comes, the Product continues each from the progress it saved
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
- text: The Product loads the remaining bytes
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
---

# Continue after a restart

## Trigger

The server or the container restarts during a download.

## Outcome

Downloads resume where they stopped, losing at most the last few megabytes.
