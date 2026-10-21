---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User unchecks the files they do not want and chooses Start N of M
  kind: actor
  actor: user
  entities:
  - entity: package
    as: collected
    effect: reads
    facts:
    - Name
  - entity: download
    effect: reads
    facts:
    - File name
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product moves the checked links into a new package with the same name, target folder and passwords and
    queues them; the unchecked links stay in the link grabber
  kind: product
  actor: user
  entities:
  - entity: package
    as: started
    effect: creates
    to: In the downloads
    facts:
    - Name
    - Target folder
    - Source
    - Source page
    - Passwords
  - entity: download
    effect: changes
    from: In the link grabber
    to: Waiting
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Start the checked files

## Trigger

Only some files of a package are wanted now.

## Outcome

The checked files download into the package folder; the rest waits in the link grabber.

## Edge cases

- When only some parts of a multi-part archive are checked, the package says the archive cannot be extracted like this and offers Check all parts.
- The checkboxes are remembered in this browser until the package is started or discarded.
