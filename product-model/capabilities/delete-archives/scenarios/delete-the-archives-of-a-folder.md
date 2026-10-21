---
kind: primary
routes:
  web: Haul web
steps:
- text: The User selects folders with archives left, chooses Delete archives and confirms
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
    - Archive files
  contexts:
    web:
      place: haul-web::signed-in::done
- text: The Product deletes every archive file directly inside them
  kind: product
  actor: user
  entities:
  - entity: archive
    effect: removes
  - entity: file
    effect: removes
    with: archive
  - entity: folder
    effect: changes
    facts:
    - Archive files
    - State
    - Size
  contexts:
    web:
      place: haul-web::signed-in::done
---

# Delete the archives of a folder

## Trigger

The archives are extracted and only take space.

## Outcome

The folders keep their contents without the archives.
