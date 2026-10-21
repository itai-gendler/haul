---
kind: edge
routes:
  web: Haul web
steps:
- text: A part of an archive is missing from the numbering, or the last part says another one follows
  kind: condition
  unattended: true
  entities:
  - entity: archive
    effect: reads
    facts:
    - Missing parts
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product extracts the complete sets and leaves that archive alone, without trying passwords on it
  kind: product
  entities:
  - entity: package
    effect: changes
    from: In the downloads
    to: Extracting
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product marks the package Extraction failed, naming the missing part
  kind: product
  entities:
  - entity: package
    effect: changes
    from: Extracting
    to: Extraction failed
    facts:
    - Extraction error
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Leave an incomplete archive alone

## Trigger

Not every part of a multi-part archive was downloaded.

## Outcome

The package says, for example, archive incomplete, missing: Movie.part02.rar.
