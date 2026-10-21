---
kind: primary
routes:
  web: Haul web
steps:
- text: The User selects a folder, chooses Delete and confirms deleting it with everything in it
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::done
- text: The Product deletes the folder and its contents from the disk
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: removes
  - entity: file
    effect: removes
    with: folder
  contexts:
    web:
      place: haul-web::signed-in::done
---

# Delete a folder

## Trigger

Finished files are no longer needed.

## Outcome

The folder is gone from the disk.
