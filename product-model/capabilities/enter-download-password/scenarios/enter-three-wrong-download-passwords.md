---
kind: edge
routes:
  web: Haul web
steps:
- text: The User answers the question a third time with a password the hoster rejects
  kind: actor
  actor: user
  entities:
  - entity: password-question
    effect: reads
    facts:
    - Download name
  contexts:
    web:
      place: haul-web::signed-in
- text: The Product marks the download failed with wrong password and forgets the password
  kind: product
  actor: user
  entities:
  - entity: password-question
    effect: removes
  - entity: download
    effect: changes
    from: Connecting
    to: Failed
    facts:
    - Download password
    - Error
  contexts:
    web:
      place: haul-web::signed-in
---

# Enter three wrong download passwords

## Trigger

The user does not know the password.

## Outcome

The download fails; resuming it asks again.
