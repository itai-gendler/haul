---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Test Click'n'Load in this browser
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The Product says Haul's browser extension handles Click'n'Load in this browser
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Test with the extension installed

## Trigger

The user wants to know whether Click'n'Load buttons will reach Haul.

## Outcome

The user knows the extension takes care of it.
