---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Cancel next to an archive password question
  kind: actor
  actor: user
  entities:
  - entity: archive-password-question
    effect: reads
    facts:
    - Archive name
  contexts:
    web:
      place: haul-web::signed-in
- text: The Product removes the question and marks the package Extraction failed with the error it had
  kind: product
  actor: user
  entities:
  - entity: archive-password-question
    effect: removes
  - entity: package
    effect: changes
    from: Extracting
    to: Extraction failed
    facts:
    - Extraction error
  contexts:
    web:
      place: haul-web::signed-in
---

# Cancel an archive password question

## Trigger

The user does not know the archive's password.

## Outcome

The archive stays unextracted; Extract again tries the known passwords and asks once more.
