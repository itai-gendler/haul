---
kind: alternate
routes:
  web: Haul web
steps:
- text: Haul starts for the first time with a login set in its configuration
  kind: condition
  unattended: true
  entities: []
  contexts:
    web:
      place: haul-web::signed-out::login
- text: The Product creates the login from them
  kind: product
  entities:
  - entity: user
    effect: creates
    facts:
    - User name
    - Password
  contexts:
    web:
      place: haul-web::signed-out::login
- text: The page asks to log in instead of creating a user
  kind: condition
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-out::login
---

# Create the login at the first start

## Trigger

The server is started with a login set in its configuration and no login exists yet.

## Outcome

The login exists before anyone opens the web interface.

## Edge cases

- A login that already exists is kept; the configured one is ignored.
