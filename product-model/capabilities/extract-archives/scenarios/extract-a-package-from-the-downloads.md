---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Extract again on a package whose extraction failed, or Extract on a finished one
  kind: actor
  actor: user
  entities:
  - entity: package
    effect: reads
    facts:
    - Name
    - Extraction error
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product extracts the package's archives again, showing the percentage
  kind: product
  actor: user
  entities:
  - entity: package
    effect: changes
    from: Extraction failed
    to: Extracting
    facts:
    - Extraction error
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The archives open and the Product marks the package extracted
  kind: product
  actor: user
  entities:
  - entity: file
    effect: creates
    facts:
    - Name
    - Path
    - Size
    - Modified
  - entity: package
    effect: changes
    from: Extracting
    to: Extracted
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Extract a package from the downloads

## Trigger

An extractor was missing, or a password has been added since.

## Outcome

The archives' contents are in the package folder and the error is gone.

## Edge cases

- Extract is offered only when every download of the package is finished and no extraction runs.
