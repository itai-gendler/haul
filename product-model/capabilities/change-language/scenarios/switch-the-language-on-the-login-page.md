---
kind: primary
routes:
  web: Haul web
steps:
- text: The User picks DE or EN on the login page
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-out::login
- text: The Product shows every text in that language in this browser from now on
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-out::login
---

# Switch the language on the login page

## Trigger

The user prefers the other language before signing in.

## Outcome

The login page and everything after it is in the chosen language.

## Edge cases

- Without a choice the browser's own language decides: German for German, otherwise English.
