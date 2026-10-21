---
kind: primary
routes:
  web: Haul web
steps:
- text: The User types a new Package name and leaves the field
  kind: actor
  actor: user
  entities:
  - entity: package
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product saves the name
  kind: product
  actor: user
  entities:
  - entity: package
    effect: changes
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Rename a package

## Trigger

The derived package name is not what the user wants.

## Outcome

The package carries the new name; a folder crawl later does not replace it.

## Edge cases

- An empty name is ignored and the old one stays.
