---
kind: validation
routes:
  extension: Browser extension
steps:
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
- text: The User sends a link from the right-click menu
  kind: actor
  actor: user
  entities: []
  contexts:
    extension:
      place: browser-extension
- text: The toolbar icon shows ! and the extension opens its options page
  kind: product
  actor: user
  entities: []
  contexts:
    extension:
      place: browser-extension::options
---

# Send links before setting up

## Trigger

The extension was just installed.

## Outcome

Nothing is sent; the user is asked to set the extension up.

## Edge cases

- When Haul rejects the API token, the icon shows ! and the settings open the same way.
- When Haul cannot be reached, the icon shows ! with that reason.
