---
kind: edge
routes:
  web: Haul web
steps:
- text: The User answers the third question with a password that does not open the archive
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
- text: The Product stops asking and marks the package Extraction failed with wrong password
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
      place: haul-web::signed-in::downloads
---

# Enter a wrong archive password

## Trigger

None of the user's guesses is right.

## Outcome

The package shows Extraction failed; Extract again asks once more.

## Edge cases

- After a wrong answer the question comes back saying the password was wrong, three times in all.
- Ten minutes without an answer end the extraction as it failed.
