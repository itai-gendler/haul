---
kind: primary
routes:
  web: Haul web
steps:
- text: The banner says a download needs a password, naming the file, the hoster and the minutes left
  kind: condition
  entities:
  - entity: password-question
    effect: reads
    facts:
    - Download name
    - Hoster
    - Time left
  - entity: download
    effect: reads
    facts:
    - File name
  contexts:
    web:
      place: haul-web::signed-in
- text: The User types the password and chooses OK
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
- text: The Product hands it to the hoster plugin, keeps it with the download and removes the question
  kind: product
  actor: user
  entities:
  - entity: password-question
    effect: removes
  - entity: download
    effect: changes
    facts:
    - Download password
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in
- text: The hoster accepts it and the download continues
  kind: product
  actor: user
  entities:
  - entity: download
    effect: changes
    from: Connecting
    to: Downloading
    facts:
    - Progress
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Enter the download password

## Trigger

A hoster asked for the password of a protected file.

## Outcome

The download loads, and the password is tried first on the package's archives as well.
