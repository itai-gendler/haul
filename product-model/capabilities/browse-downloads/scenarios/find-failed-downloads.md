---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses the Failed filter and searches for a file name
  kind: actor
  actor: user
  entities:
  - entity: download
    effect: reads
    facts:
    - File name
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product shows only the failed downloads that match, each with why it failed
  kind: product
  actor: user
  entities:
  - entity: download
    effect: reads
    facts:
    - File name
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Find failed downloads

## Trigger

Some downloads failed among many.

## Outcome

The user sees which ones failed and why.
