---
kind: primary
routes:
  web: Haul web
steps:
- text: The banner says an archive needs a password, naming the archive, its package and the minutes left
  kind: condition
  entities:
  - entity: archive-password-question
    effect: reads
    facts:
    - Archive name
    - Package name
    - Time left
  - entity: package
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in
- text: The User types the password and chooses OK
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
- text: The Product opens the archive with it and extracts it
  kind: product
  actor: user
  entities:
  - entity: archive-password-question
    effect: removes
  - entity: file
    effect: creates
    facts:
    - Name
    - Path
    - Size
    - Modified
  contexts:
    web:
      place: haul-web::signed-in
- text: The Product puts the password at the top of the archive passwords and marks the package extracted
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - Archive passwords
  - entity: package
    effect: changes
    from: Extracting
    to: Extracted
    facts:
    - Extraction error
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Enter the archive password

## Trigger

An archive's password is not among those Haul knows.

## Outcome

The archive is extracted, and the password is tried first on the next protected archive.
