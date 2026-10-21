---
kind: alternate
routes:
  web: Haul web
steps:
- text: A download of a direct link reaches the front of the queue
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts:
    - Link
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product asks the link's server directly for the bytes
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Waiting
    to: Connecting
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product names the file from the server's answer or the link and loads it
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Connecting
    to: Downloading
    facts:
    - File name
    - Size
    - Progress
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product moves the finished file into the package folder
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

# Download a direct link

## Trigger

The link points straight at a file.

## Outcome

The file is in the package folder.
