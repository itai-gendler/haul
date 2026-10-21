---
kind: primary
routes:
  web: Haul web
steps:
- text: The User enters the user name and the password and chooses Log in
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-out::login
- text: The Product checks them and starts a login that lasts 30 days in this browser
  kind: product
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - User name
    - Password
  contexts:
    web:
      place: haul-web::signed-out::login
---

# Log in with the login

## Trigger

The user opens Haul while signed out.

## Outcome

The user is signed in and sees the downloads.
