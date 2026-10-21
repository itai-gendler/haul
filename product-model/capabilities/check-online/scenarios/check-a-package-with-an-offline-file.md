---
kind: edge
routes:
  web: Haul web
steps:
- text: The User chooses Check online on a package
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
- text: The hoster says one of the files is gone
  kind: condition
  entities:
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product marks that link File offline with the hoster's message
  kind: product
  actor: user
  entities:
  - entity: download
    effect: changes
    facts:
    - Online status
    - Error
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Check a package with an offline file

## Trigger

A file of the package was deleted at the hoster.

## Outcome

The link shows File offline, and the package counts it as offline; starting leaves it out.

## Edge cases

- A hoster that cannot tell leaves the link Unchecked, with its message.
