---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Pause on a package
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
- text: The Product pauses its downloads that are waiting, connecting or downloading
  kind: product
  actor: user
  entities:
  - entity: download
    effect: changes
    from: Waiting
    to: Paused
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Pause a package

## Trigger

One package should wait.

## Outcome

The package's unfinished downloads are paused; other packages go on.
