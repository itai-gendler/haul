---
kind: primary
routes:
  web: Haul web
steps:
- text: A slot is free and a download whose hoster has no usable account waits at the front of the queue
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts:
    - Next try
  - entity: settings
    effect: reads
    facts:
    - Parallel downloads
  - entity: account
    effect: reads
    facts:
    - Active
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product has the link's hoster plugin get the direct address as a guest
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Waiting
    to: Connecting
    facts: []
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product loads the bytes over several connections at once, keeping the progress as it goes
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
  - entity: settings
    effect: reads
    facts:
    - Connections per file
    - Bandwidth limit
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product moves the finished file into the package's target folder, under a free name if the name is taken
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Downloading
    to: Finished
    facts:
    - File name
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

# Download a hoster link

## Trigger

The user started a package with hoster links.

## Outcome

The file is in the package folder and the download shows Finished.

## Edge cases

- Simple text captchas of some hosters are read by Haul itself.
- A free download waits out the countdown the hoster shows before it gets the address.
- A file the hoster sends encrypted is decrypted as it is saved, also when it resumes.
- A hoster that answers with a web page instead of the file counts as a failed attempt, with the page's text as the reason.
