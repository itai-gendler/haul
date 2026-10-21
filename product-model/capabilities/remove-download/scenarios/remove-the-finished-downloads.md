---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Remove finished
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product removes every finished download from the list and leaves the files on disk
  kind: product
  actor: user
  entities:
  - entity: download
    effect: removes
    from: Finished
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product drops each package left empty
  kind: product
  actor: user
  entities:
  - entity: package
    effect: removes
    from: Extracted
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Remove the finished downloads

## Trigger

The list is full of finished downloads.

## Outcome

Only unfinished downloads remain listed; the files are still in the done folder.
