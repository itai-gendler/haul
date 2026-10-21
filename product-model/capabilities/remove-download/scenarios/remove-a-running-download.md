---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Remove on a download that is loading
  kind: actor
  actor: user
  entities:
  - entity: download
    effect: reads
    facts:
    - File name
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product stops it, deletes the partial data and removes it from the list
  kind: product
  actor: user
  entities:
  - entity: download
    effect: removes
    from: Downloading
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Remove a running download

## Trigger

The user no longer wants a file that is downloading.

## Outcome

The download is gone and its slot is free for the next one.
