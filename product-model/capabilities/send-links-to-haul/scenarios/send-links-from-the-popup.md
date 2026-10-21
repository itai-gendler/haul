---
kind: alternate
routes:
  extension: Browser extension
steps:
- text: The User pastes links into the popup and chooses Send links
  kind: actor
  actor: user
  entities: []
  contexts:
    extension:
      place: browser-extension::popup
- text: The extension sends the links it finds in the text
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
      place: browser-extension::popup
- text: The Product puts them in a new package in the link grabber and the popup says how many were sent
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
      place: browser-extension::popup
---

# Send links from the popup

## Trigger

The user has links copied from somewhere else.

## Outcome

The links wait in the link grabber; the popup field is cleared.

## Edge cases

- Send this page sends the current tab's address.
