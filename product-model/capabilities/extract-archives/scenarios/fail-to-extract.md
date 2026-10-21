---
kind: edge
routes:
  web: Haul web
steps:
- text: The last download of a package with archives finishes
  kind: condition
  unattended: true
  entities:
  - entity: package
    effect: reads
    facts: []
  - entity: download
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product starts extracting the package
  kind: product
  entities:
  - entity: package
    effect: changes
    from: In the downloads
    to: Extracting
    facts: []
  - entity: archive
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The archive is damaged, the disk is full or no extractor can open it
  kind: condition
  entities:
  - entity: archive
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product marks the package Extraction failed with the most likely cause first and what each extractor
    that was tried said
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

# Fail to extract

## Trigger

An archive cannot be opened.

## Outcome

The package shows Extraction failed with the reason and offers Extract again.

## Edge cases

- After a restart an extraction that was running starts again.
