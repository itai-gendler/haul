---
kind: edge
routes:
  web: Haul web
steps:
- text: Some links of the package are File offline
  kind: condition
  entities:
  - entity: download
    effect: reads
    facts:
    - Online status
  - entity: package
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The User chooses Start N, which counts only the links that are not offline
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
- text: The Product queues only the links that are not offline
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

# Start a package with offline files

## Trigger

The online check found files that are gone.

## Outcome

The available files download; the offline links are not tried.

## Edge cases

- A package with no link left to start cannot be started.
