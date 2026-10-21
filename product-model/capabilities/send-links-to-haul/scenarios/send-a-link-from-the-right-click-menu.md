---
kind: primary
routes:
  extension: Browser extension
steps:
- text: The User right-clicks a link on a page and chooses Send link to Haul
  kind: actor
  actor: user
  entities: []
  contexts:
    extension:
      place: browser-extension
- text: The extension sends it to the Haul address with the API token
  kind: product
  actor: user
  entities:
  - entity: extension-settings
    effect: reads
    facts:
    - Haul address
    - API token
    - Start sent links right away
  contexts:
    extension:
      place: browser-extension
- text: The Product puts it in a new package in the link grabber with the page it came from
  kind: product
  actor: user
  entities:
  - entity: package
    effect: creates
    to: In the link grabber
    facts:
    - Name
    - Target folder
    - Source
    - Source page
  - entity: download
    effect: creates
    to: In the link grabber
    facts:
    - Link
    - File name
    - Hoster
    - Online status
    with: package
  contexts:
    extension:
      place: browser-extension
- text: The toolbar icon shows a check mark for a few seconds
  kind: product
  actor: user
  entities: []
  contexts:
    extension:
      place: browser-extension
---

# Send a link from the right-click menu

## Trigger

The user finds a download link while browsing.

## Outcome

The link waits in Haul's link grabber, checked online, with its source page.
