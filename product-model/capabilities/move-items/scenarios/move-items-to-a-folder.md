---
kind: primary
routes:
  web: Haul web
steps:
- text: The User selects files and folders, chooses Move… and picks a target folder
  kind: actor
  actor: user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
  - entity: folder
    effect: reads
    facts:
    - Name
    - Path
  contexts:
    web:
      place: haul-web::signed-in::done
- text: The Product moves them there, giving a taken name a number
  kind: product
  actor: user
  entities:
  - entity: file
    effect: changes
    facts:
    - Path
    - Name
  - entity: folder
    effect: changes
    facts:
    - Path
    - Name
  contexts:
    web:
      place: haul-web::signed-in::done
---

# Move items to a folder

## Trigger

The user sorts finished downloads.

## Outcome

The items are in the target folder.

## Edge cases

- A folder cannot be moved into itself.
