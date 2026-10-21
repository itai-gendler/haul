---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Start on a package with every file checked
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
- text: The Product moves the package to the downloads and queues its links
  kind: product
  actor: user
  entities:
  - entity: package
    effect: changes
    from: In the link grabber
    to: In the downloads
    facts: []
  - entity: download
    effect: changes
    from: In the link grabber
    to: Waiting
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Start a package

## Trigger

The user is happy with the package.

## Outcome

The package is in the downloads and its links wait for a free slot.
