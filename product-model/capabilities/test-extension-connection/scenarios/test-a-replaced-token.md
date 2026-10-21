---
kind: edge
routes:
  extension: Browser extension
steps:
- text: The User chooses Test connection with a token Haul no longer accepts
  kind: actor
  actor: user
  entities:
  - entity: extension-settings
    effect: reads
    facts:
    - API token
  contexts:
    extension:
      place: browser-extension::options
- text: The extension says Haul rejected the API token
  kind: product
  actor: user
  entities: []
  contexts:
    extension:
      place: browser-extension::options
---

# Test a replaced token

## Trigger

A new token was created in Haul.

## Outcome

The user knows to paste the new token; a wrong address says Haul is not reachable instead.
