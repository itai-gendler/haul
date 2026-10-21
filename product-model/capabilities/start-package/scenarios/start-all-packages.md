---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Start all, or Start checked when some files are unchecked
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product starts each package that has a checked file, the way Start does
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

# Start all packages

## Trigger

Everything in the link grabber should download.

## Outcome

Every package with a checked file is in the downloads.
