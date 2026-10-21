---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User selects archive files or folders with archives in the Done view and chooses Extract
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
    - Archive files
  - entity: archive
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::done
- text: The Product extracts each selected set once, whichever part was picked, into the folder it is in, one job
    after the other
  kind: product
  actor: user
  entities:
  - entity: archive
    effect: reads
    facts:
    - Name
    - Parts
  - entity: file
    effect: creates
    facts:
    - Name
    - Path
    - Size
    - Modified
  contexts:
    web:
      place: haul-web::signed-in::done
- text: The Product shows the percentage in the folder and then the folder's new state
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: changes
    facts:
    - State
    - Size
    - Modified
  contexts:
    web:
      place: haul-web::signed-in::done
---

# Extract from the Done view

## Trigger

Archives in the done folder were not extracted, or came from elsewhere.

## Outcome

The contents are next to the archives and the folder shows extracted.

## Edge cases

- A folder that belongs to a package is extracted as that package, with its passwords and state.
- A folder already being extracted is refused with a message.
