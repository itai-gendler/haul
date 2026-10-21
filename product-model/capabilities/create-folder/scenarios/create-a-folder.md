---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses New folder, enters a name and chooses Create
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::done
- text: The Product creates the folder
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: creates
    facts:
    - Name
    - Path
  contexts:
    web:
      place: haul-web::signed-in::done
---

# Create a folder

## Trigger

The user wants a place to sort files into.

## Outcome

The new folder is listed.
