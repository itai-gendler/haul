---
kind: alternate
routes:
  web: Haul web
steps:
- text: No known password opens an archive and Ask for the archive password when none fits is on
  kind: condition
  unattended: true
  entities:
  - entity: settings
    effect: reads
    facts:
    - Ask for the archive password when none fits
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product asks in the banner for the archive's password, naming the archive and its package
  kind: product
  entities:
  - entity: archive-password-question
    effect: creates
    facts:
    - Archive name
    - Package name
    - Wrong before
    - Time left
  - entity: package
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in
---

# Ask for an archive password

## Trigger

A protected archive's password is not among those Haul knows.

## Outcome

The extraction waits for the user's answer, at most ten minutes.
