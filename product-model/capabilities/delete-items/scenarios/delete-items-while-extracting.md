---
kind: validation
routes:
  web: Haul web
steps:
- text: The User tries to delete a folder in which, or around which, an extraction runs
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
    - State
  contexts:
    web:
      place: haul-web::signed-in::done
- text: The Product refuses and says the folder is being extracted; nothing is deleted
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::done
---

# Delete items while extracting

## Trigger

An extraction is still running.

## Outcome

Everything stays on disk.
