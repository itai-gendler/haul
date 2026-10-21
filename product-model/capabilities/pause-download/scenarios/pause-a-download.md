---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Pause on a download that is loading
  kind: actor
  actor: user
  entities:
  - entity: download
    effect: reads
    facts:
    - File name
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product stops it and keeps the bytes that arrived
  kind: product
  actor: user
  entities:
  - entity: download
    effect: changes
    from: Downloading
    to: Paused
    facts:
    - Progress
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Pause a download

## Trigger

The user needs the bandwidth for something else.

## Outcome

The download shows Paused and its slot goes to the next waiting one.

## Edge cases

- A captcha or password question the download was waiting on leaves the banner.
