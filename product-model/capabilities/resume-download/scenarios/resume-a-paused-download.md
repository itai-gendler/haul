---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Resume on a paused download
  kind: actor
  actor: user
  entities:
  - entity: download
    effect: reads
    facts:
    - File name
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product puts it back in the queue with its retries counted from zero
  kind: product
  actor: user
  entities:
  - entity: download
    effect: changes
    from: Paused
    to: Waiting
    facts:
    - Attempts
    - Next try
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Resume a paused download

## Trigger

The user wants a paused download to go on.

## Outcome

The download waits for a slot and then continues where it stopped.
