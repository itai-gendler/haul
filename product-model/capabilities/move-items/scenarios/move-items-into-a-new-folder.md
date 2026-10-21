---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User selects items, chooses Move… and names a new folder inside the target
  kind: actor
  actor: user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::done
- text: The Product creates the folder and moves the items into it
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: creates
    facts:
    - Name
    - Path
  - entity: file
    effect: changes
    facts:
    - Path
    - Name
  contexts:
    web:
      place: haul-web::signed-in::done
---

# Move items into a new folder

## Trigger

There is no folder for the items yet.

## Outcome

The items are in the new folder.
