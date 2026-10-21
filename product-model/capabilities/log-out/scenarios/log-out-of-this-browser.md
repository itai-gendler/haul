---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Log out in the Login section
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The Product ends this browser's login and shows the login page
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Log out of this browser

## Trigger

The user is done with Haul in this browser.

## Outcome

The browser is signed out; downloads keep running on the server.
