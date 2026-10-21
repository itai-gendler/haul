---
kind: validation
routes:
  web: Haul web
steps:
- text: The User enters a user name and a password shorter than 8 characters
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-out::login
- text: The Product refuses and asks for a user name and a password of at least 8 characters
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-out::login
---

# Create the login with a short password

## Trigger

The first user is created with a password that is too short.

## Outcome

No login exists yet and the page still asks to create one.
