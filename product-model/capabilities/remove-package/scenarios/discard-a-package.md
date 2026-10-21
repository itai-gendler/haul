---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Discard on a package in the link grabber
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
- text: The Product removes the package and its links
  kind: product
  actor: user
  entities:
  - entity: package
    effect: removes
    from: In the link grabber
  - entity: download
    effect: removes
    from: In the link grabber
    with: package
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Discard a package

## Trigger

The links are not wanted after all.

## Outcome

The package is gone from the link grabber.
