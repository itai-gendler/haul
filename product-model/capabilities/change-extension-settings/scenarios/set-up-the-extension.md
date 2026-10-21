---
kind: primary
routes:
  extension: Browser extension
steps:
- text: The User enters the Haul address and the API token and chooses Save
  kind: actor
  actor: user
  entities:
  - entity: extension-settings
    effect: reads
    facts:
    - Haul address
    - API token
    - Handle Click'n'Load buttons
    - Start sent links right away
  contexts:
    extension:
      place: browser-extension::options
- text: The User allows the access to the Haul server the browser asks for, and to all websites for Click'n'Load
    where the browser has not granted it
  kind: actor
  actor: user
  entities: []
  contexts:
    extension:
      place: browser-extension::options
- text: The extension saves them and shows Connected with the active and queued downloads
  kind: product
  actor: user
  entities:
  - entity: extension-settings
    effect: changes
    facts:
    - Haul address
    - API token
    - Handle Click'n'Load buttons
    - Start sent links right away
  - entity: download
    effect: reads
    facts: []
  contexts:
    extension:
      place: browser-extension::options
---

# Set up the extension

## Trigger

The user installed the extension.

## Outcome

Links and Click'n'Load buttons go to the user's Haul.
