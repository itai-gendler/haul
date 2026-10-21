---
kind: validation
routes:
  web: Haul web
steps:
- text: The User enters a name that is already taken in this folder
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
- text: The Product refuses and says the name exists
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::done
---

# Create a folder whose name exists

## Trigger

A folder of that name already exists here.

## Outcome

Nothing is created.

## Edge cases

- A name with a path separator, or . or .., is refused as invalid.
