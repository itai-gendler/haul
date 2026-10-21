---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Cancel next to a password question
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
- text: The Product removes the question and marks the download failed with password entry cancelled
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
    - Error
  contexts:
    web:
      place: haul-web::signed-in
---

# Cancel a download password question

## Trigger

The user has no password for the file.

## Outcome

The download fails at once instead of asking again later.
