---
kind: primary
result: achieved
routes:
  extension: Browser extension
steps:
- text: The User right-clicks a link and chooses Send link to Haul
  kind: actor
  actor: user
  capability: send-links-to-haul
  entities: []
  contexts:
    extension:
      place: browser-extension
- text: The extension has no Haul address or API token yet
  kind: condition
  entities:
  - entity: extension-settings
    effect: reads
    facts:
    - Haul address
    - API token
  contexts:
    extension:
      place: browser-extension
- text: The toolbar icon shows ! and the extension opens its options page
  kind: product
  actor: user
  capability: send-links-to-haul
  entities: []
  contexts:
    extension:
      place: browser-extension::options
- text: The User enters the Haul address and the API token and chooses Save
  kind: actor
  actor: user
  capability: change-extension-settings
  entities:
  - entity: extension-settings
    effect: reads
    facts:
    - Haul address
    - API token
  contexts:
    extension:
      place: browser-extension::options
- text: The extension saves them and shows Connected
  kind: product
  actor: user
  capability: change-extension-settings
  entities:
  - entity: extension-settings
    effect: changes
    facts:
    - Haul address
    - API token
  contexts:
    extension:
      place: browser-extension::options
- text: The User sends the link again from the right-click menu
  kind: actor
  actor: user
  capability: send-links-to-haul
  entities: []
  contexts:
    extension:
      place: browser-extension
- text: The Product puts it in a new package in the link grabber
  kind: product
  actor: user
  capability: send-links-to-haul
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

# Send a link before the extension is set up

## Trigger

The user tries the new extension right away.

## Outcome

The link is in the link grabber and later sends work at once.
