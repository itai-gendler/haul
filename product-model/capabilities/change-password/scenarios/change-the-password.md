---
kind: primary
routes:
  web: Haul web
steps:
- text: The User enters the current password and a new one of at least 8 characters and chooses Change password
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The Product checks the current password and saves the new one
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Password
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Change the password

## Trigger

The user wants a different login password.

## Outcome

The new password opens the login from now on; the page says the password was changed.
