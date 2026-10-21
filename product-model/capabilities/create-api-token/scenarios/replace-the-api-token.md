---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Create new token while one is set
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
- text: The Product replaces the token and shows the new one once; the old one stops working
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

# Replace the API token

## Trigger

The old token was lost or should no longer work.

## Outcome

Only the new token is accepted; the extension says the token was replaced until it gets the new one.
