---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Resume all while nothing is running
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product queues every paused download again
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

# Resume all

## Trigger

The user paused everything earlier.

## Outcome

Every paused download waits for a slot again; failed ones stay failed.
