---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Pause all
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product pauses every download that is waiting, connecting or downloading
  kind: product
  actor: user
  entities:
  - entity: download
    effect: changes
    from: Connecting
    to: Paused
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Pause all

## Trigger

Everything should stop for now.

## Outcome

Nothing downloads until the user resumes.
