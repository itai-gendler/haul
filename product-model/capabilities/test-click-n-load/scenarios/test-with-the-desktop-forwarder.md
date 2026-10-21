---
kind: alternate
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
- text: The Product finds the Click'n'Load port answering and says whether Haul itself or the desktop forwarder
    listens there
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Test with the desktop forwarder

## Trigger

The user runs the desktop forwarder or Haul on the same machine.

## Outcome

The user knows which program answers.
