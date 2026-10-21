---
kind: alternate
routes:
  web: Haul web
steps:
- text: A download whose hoster published a checksum has all its bytes and Verify the checksum is on
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts:
    - Checksum
  - entity: settings
    effect: reads
    facts:
    - Verify the checksum
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product waits for its turn, since one check runs at a time, and checks the file against the hoster's
    value
  kind: product
  entities:
  - entity: download
    effect: changes
    facts:
    - Checksum result
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The value matches; the Product moves the file into the package folder and shows it verified
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Downloading
    to: Finished
    facts:
    - Finished at
  - entity: file
    effect: creates
    facts:
    - Name
    - Path
    - Size
    - Modified
  - entity: package
    effect: reads
    facts:
    - Target folder
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Verify the checksum

## Trigger

The file comes from a hoster that lists checksums.

## Outcome

The download shows verified next to its name.
