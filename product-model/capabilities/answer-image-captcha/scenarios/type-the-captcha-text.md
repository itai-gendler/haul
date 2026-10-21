---
kind: primary
routes:
  web: Haul web
steps:
- text: The banner shows a picture with text, the hoster and the minutes left
  kind: condition
  entities:
  - entity: image-captcha
    effect: reads
    facts:
    - Picture
    - Hoster
    - Time left
  contexts:
    web:
      place: haul-web::signed-in
- text: The User types the text shown in the picture and chooses OK
  kind: actor
  actor: user
  entities:
  - entity: image-captcha
    effect: reads
    facts:
    - Picture
  contexts:
    web:
      place: haul-web::signed-in
- text: The Product hands the text to the hoster plugin and the download goes on
  kind: product
  actor: user
  entities:
  - entity: image-captcha
    effect: removes
  - entity: download
    effect: reads
    facts:
    - File name
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in
---

# Type the captcha text

## Trigger

A hoster asked for the text in a picture.

## Outcome

The download continues by itself.
