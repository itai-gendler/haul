---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User types a password and chooses OK
  kind: actor
  actor: user
  entities:
  - entity: password-question
    as: first
    effect: reads
    facts:
    - Download name
  contexts:
    web:
      place: haul-web::signed-in
- text: The hoster rejects it; the Product forgets it and asks again, saying the password was wrong
  kind: product
  actor: user
  entities:
  - entity: password-question
    as: first
    effect: removes
  - entity: password-question
    as: second
    effect: creates
    facts:
    - Download name
    - Hoster
    - Wrong before
    - Time left
  - entity: download
    effect: changes
    facts:
    - Download password
  contexts:
    web:
      place: haul-web::signed-in
- text: The User types the right password and chooses OK
  kind: actor
  actor: user
  entities:
  - entity: password-question
    as: second
    effect: reads
    facts:
    - Download name
  contexts:
    web:
      place: haul-web::signed-in
- text: The Product keeps it and the download continues
  kind: product
  actor: user
  entities:
  - entity: password-question
    as: second
    effect: removes
  - entity: download
    effect: changes
    from: Connecting
    to: Downloading
    facts:
    - Download password
    - Progress
  contexts:
    web:
      place: haul-web::signed-in
---

# Enter a wrong download password

## Trigger

The first password the user tries is not the right one.

## Outcome

The download continues with the right password.
