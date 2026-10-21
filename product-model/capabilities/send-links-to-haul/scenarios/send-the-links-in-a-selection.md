---
kind: alternate
routes:
  extension: Browser extension
steps:
- text: The User selects part of a page and chooses Send links in selection to Haul
  kind: actor
  actor: user
  entities: []
  contexts:
    extension:
      place: browser-extension
- text: The extension collects every link in the selection, also those only written as text, and sends them
  kind: product
  actor: user
  entities:
  - entity: extension-settings
    effect: reads
    facts:
    - Haul address
    - API token
  contexts:
    extension:
      place: browser-extension
- text: The Product puts them in one new package in the link grabber
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
---

# Send the links in a selection

## Trigger

A page lists many links.

## Outcome

All selected links wait together in the link grabber.

## Edge cases

- Send page to Haul sends the address of the page itself.
