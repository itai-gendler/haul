---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Create token
  kind: actor
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - API token
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The Product creates a token, shows it once together with the desktop forwarder's command line, and keeps
    only a fingerprint of it
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - API token
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Create the API token

## Trigger

The user sets up the browser extension or the desktop forwarder.

## Outcome

The user copies the token; afterwards the page says only that a token is set.
