---
kind: alternate
routes:
  extension: Browser extension
steps:
- text: The User turns off Handle Click'n'Load buttons and chooses Save
  kind: actor
  actor: user
  entities:
  - entity: extension-settings
    effect: reads
    facts:
    - Handle Click'n'Load buttons
  contexts:
    extension:
      place: browser-extension::options
- text: The extension saves it and no longer takes Click'n'Load requests from pages
  kind: product
  actor: user
  entities:
  - entity: extension-settings
    effect: changes
    facts:
    - Handle Click'n'Load buttons
  contexts:
    extension:
      place: browser-extension::options
---

# Switch off Click'n'Load in the extension

## Trigger

The desktop forwarder or another download manager handles Click'n'Load on this computer.

## Outcome

Click'n'Load buttons reach the local port as before; Send to Haul still works.
