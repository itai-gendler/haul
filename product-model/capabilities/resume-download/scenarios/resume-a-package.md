---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Resume on a package
  kind: actor
  actor: user
  entities:
  - entity: package
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product queues its paused and failed downloads again
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

# Resume a package

## Trigger

A paused package should go on.

## Outcome

The package's downloads wait for slots again.
