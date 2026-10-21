---
kind: validation
routes:
  extension: Browser extension
steps:
- text: The User chooses Save and declines the access the browser asks for
  kind: actor
  actor: user
  entities:
  - entity: extension-settings
    effect: reads
    facts:
    - Haul address
  contexts:
    extension:
      place: browser-extension::options
- text: The extension keeps what was saved before and says it needs permission to reach Haul
  kind: product
  actor: user
  entities: []
  contexts:
    extension:
      place: browser-extension::options
---

# Decline the browser permission

## Trigger

The user declined the browser's prompt.

## Outcome

Nothing changes.

## Edge cases

- An address that is not a valid address is refused before the browser asks anything.
