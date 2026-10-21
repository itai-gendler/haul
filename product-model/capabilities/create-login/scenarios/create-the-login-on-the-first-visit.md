---
kind: primary
routes:
  web: Haul web
steps:
- text: No login exists yet, so the page asks to create one
  kind: condition
  entities: []
  contexts:
    web:
      place: haul-web::signed-out::login
- text: The User enters a user name and a password of at least 8 characters and chooses Create user
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-out::login
- text: The Product creates the login and signs the User in
  kind: product
  actor: user
  entities:
  - entity: user
    effect: creates
    facts:
    - User name
    - Password
  contexts:
    web:
      place: haul-web::signed-out::login
---

# Create the login on the first visit

## Trigger

Haul is opened in the browser for the first time.

## Outcome

The one login exists and the user is signed in.
