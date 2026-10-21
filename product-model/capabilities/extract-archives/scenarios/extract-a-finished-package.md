---
kind: primary
routes:
  web: Haul web
steps:
- text: The last download of a package finishes and Extract finished packages automatically is on
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts: []
  - entity: settings
    effect: reads
    facts:
    - Extract finished packages automatically
  - entity: package
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: Every part of each of the package's archives is there and none is still loading
  kind: condition
  entities:
  - entity: archive
    effect: reads
    facts:
    - Parts
    - Missing parts
  - entity: package
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product extracts the archives the package downloaded into the folder they are in, showing the percentage
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
- text: The Product tries no password, the package's passwords, the archive's name and then the archive passwords,
    and the archive opens
  kind: product
  entities:
  - entity: package
    effect: reads
    facts:
    - Passwords
  - entity: settings
    effect: reads
    facts:
    - Archive passwords
  - entity: file
    effect: creates
    facts:
    - Name
    - Path
    - Size
    - Modified
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product moves the password that opened it to the top of the archive passwords and marks the package
    extracted
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Archive passwords
  - entity: package
    effect: changes
    from: Extracting
    to: Extracted
    facts:
    - Extraction error
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Extract a finished package

## Trigger

A package with archives has finished downloading.

## Outcome

The archives' contents are in the package folder and the package shows extracted.

## Decision points

### Are the archives deleted?

Is Delete archives after successful extraction on?

- On → the Product deletes the archive files once they are extracted.
- Off → the archive files stay next to their contents.

### Do the downloads stay listed?

Is Remove the downloads from the list after successful extraction on?

- On → the Product removes the extracted parts' downloads from the list; other files of the package stay listed.
- Off → every download stays listed as finished.

## Edge cases

- Archives that another package downloaded into the same folder are left to that package.
- A package without archives is not extracted and stays as it is.
