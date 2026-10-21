---
kind: validation
routes:
  web: Haul web
steps:
- text: The User enters a current password that does not match
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The Product refuses and says the current password is wrong
  kind: product
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Password
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Change the password with a wrong current one

## Trigger

The user mistypes the old password.

## Outcome

The password stays as it was.

## Edge cases

- A new password shorter than 8 characters is refused the same way.
