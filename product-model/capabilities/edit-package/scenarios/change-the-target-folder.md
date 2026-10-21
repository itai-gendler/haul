---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User types another Target folder and leaves the field
  kind: actor
  actor: user
  entities:
  - entity: package
    effect: reads
    facts:
    - Target folder
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product saves it as a folder inside the done folder, dropping parts that would lead elsewhere
  kind: product
  actor: user
  entities:
  - entity: package
    effect: changes
    facts:
    - Target folder
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Change the target folder

## Trigger

The user wants the files in another folder, such as a shared Movies folder.

## Outcome

The package's files will land in that folder below the done folder.
