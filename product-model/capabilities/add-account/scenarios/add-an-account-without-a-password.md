---
kind: validation
routes:
  web: Haul web
steps:
- text: The User chooses Add with the password field empty
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product refuses and says the password is missing
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
---

# Add an account without a password

## Trigger

The form is incomplete.

## Outcome

No account is added.
