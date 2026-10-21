---
kind: primary
routes:
  web: Haul web
steps:
- text: The User opens Done and then a folder
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
    - State
  contexts:
    web:
      place: haul-web::signed-in::done
- text: The Product lists the folder's folders and files with size and modification date, and for each folder whether
    it is extracted, has archives left, failed, is finished or is not from Haul
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
    - Path
    - Size
    - Modified
    - Archive files
    - State
  - entity: file
    effect: reads
    facts:
    - Name
    - Size
    - Modified
  - entity: package
    effect: reads
    facts:
    - Extraction error
  contexts:
    web:
      place: haul-web::signed-in::done
---

# Open a folder

## Trigger

The user wants to see what finished.

## Outcome

The user sees the folder's contents and where extraction stands.

## Edge cases

- A folder being extracted shows its percentage instead of its state.
