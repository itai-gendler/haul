---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Remove on a link in the link grabber
  kind: actor
  actor: user
  entities:
  - entity: download
    effect: reads
    facts:
    - File name
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product removes the link from its package
  kind: product
  actor: user
  entities:
  - entity: download
    effect: removes
    from: In the link grabber
  - entity: package
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Remove a link from the link grabber

## Trigger

A pasted link is not wanted.

## Outcome

The link is gone from the package.

## Edge cases

- A package whose last link is removed disappears with it.
