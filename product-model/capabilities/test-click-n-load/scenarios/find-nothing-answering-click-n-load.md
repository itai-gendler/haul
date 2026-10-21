---
kind: edge
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
- text: The Product says the port cannot be reached and recommends the browser extension or the desktop forwarder
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Find nothing answering Click'n'Load

## Trigger

Haul runs on a server and nothing on the desktop takes Click'n'Load.

## Outcome

The user knows what to install; something else answering the port is named with its status.
