---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User picks Deutsch or English in the Language section
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The Product reloads the page and shows every text in that language, also stored errors and messages from
    the hosters
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Switch the language in settings

## Trigger

The user wants Haul in the other language.

## Outcome

Haul shows the chosen language in this browser; other browsers keep theirs.
