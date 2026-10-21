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
- text: The hoster shows a picture whose text must be typed
  kind: condition
  entities: []
  contexts:
    web:
      place: haul-web::signed-in
- text: The Product loads the picture with the plugin's session and shows it in the banner
  kind: product
  entities:
  - entity: image-captcha
    effect: creates
    facts:
    - Hoster
    - Picture
    - Time left
  contexts:
    web:
      place: haul-web::signed-in
---

# Ask for an image captcha

## Trigger

A hoster protects its download with a picture captcha.

## Outcome

The banner shows the picture and a field for its text.
