---
kind: primary
routes:
  extension: Browser extension
steps:
- text: The User chooses Test connection
  kind: actor
  actor: user
  entities:
  - entity: extension-settings
    effect: reads
    facts:
    - Haul address
    - API token
  contexts:
    extension:
      place: browser-extension::options
- text: The extension asks Haul with the token and shows Connected with the number of active and queued downloads
  kind: product
  actor: user
  entities:
  - entity: download
    effect: reads
    facts: []
  contexts:
    extension:
      place: browser-extension::options
---

# Check the connection

## Trigger

The user wants to be sure the extension is set up right.

## Outcome

The user sees Connected.
