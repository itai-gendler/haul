---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Remove on a started package
  kind: actor
  actor: user
  entities:
  - entity: package
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product stops its downloads, deletes their partial data and removes the package with them
  kind: product
  actor: user
  entities:
  - entity: package
    effect: removes
    from: In the downloads
  - entity: download
    effect: removes
    from: Downloading
    with: package
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Remove a started package

## Trigger

The user gives up on a package that is downloading.

## Outcome

The package is gone from the list; files it already finished stay in its folder.
