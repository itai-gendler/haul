---
kind: validation
routes:
  web: Haul web
steps:
- text: The User enters a user name or a password that does not match
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-out::login
- text: The Product waits a moment and says the user name or the password is wrong
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

# Log in with wrong credentials

## Trigger

The user mistypes the login.

## Outcome

The user stays signed out.
