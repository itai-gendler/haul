---
kind: alternate
routes:
  web: Haul web
steps:
- text: A queued download reaches the front of the queue
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts:
    - Next try
  contexts:
    web:
      place: haul-web::signed-in
- text: The Product has the link's hoster plugin get the direct address
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Waiting
    to: Connecting
    facts: []
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in
- text: The hoster asks for a password and the download has none, or the hoster rejected it
  kind: condition
  entities:
  - entity: download
    effect: reads
    facts:
    - Download password
  contexts:
    web:
      place: haul-web::signed-in
- text: The Product asks in the banner on every page for the password of that download
  kind: product
  entities:
  - entity: password-question
    effect: creates
    facts:
    - Download name
    - Hoster
    - Wrong before
    - Time left
  - entity: download
    effect: reads
    facts:
    - File name
  contexts:
    web:
      place: haul-web::signed-in
---

# Ask for a download password

## Trigger

A protected file or folder is downloaded without its password.

## Outcome

The download shows Waiting for password until the user answers or ten minutes pass.
