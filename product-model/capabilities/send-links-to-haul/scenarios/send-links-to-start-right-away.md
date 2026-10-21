---
kind: alternate
routes:
  extension: Browser extension
steps:
- text: Start sent links right away is on in the extension
  kind: condition
  entities:
  - entity: extension-settings
    effect: reads
    facts:
    - Start sent links right away
  contexts:
    extension:
      place: browser-extension
- text: The User sends a link from the right-click menu
  kind: actor
  actor: user
  entities: []
  contexts:
    extension:
      place: browser-extension
- text: The Product puts it in a new package that goes straight to the downloads, its link queued
  kind: product
  actor: user
  entities:
  - entity: package
    effect: creates
    to: In the downloads
    facts:
    - Name
    - Target folder
    - Source
    - Source page
  - entity: download
    effect: creates
    to: Waiting
    facts:
    - Link
    - File name
    - Hoster
    - Online status
    with: package
  contexts:
    extension:
      place: browser-extension
---

# Send links to start right away

## Trigger

The user wants sent links to download without a stop in the link grabber.

## Outcome

The link is queued at once.
