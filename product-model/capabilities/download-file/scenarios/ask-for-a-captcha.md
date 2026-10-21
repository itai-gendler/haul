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
- text: The hoster hands out the address only after a check on its own page
  kind: condition
  entities: []
  contexts:
    web:
      place: haul-web::signed-in
- text: The Product puts the captcha in the banner on every page, in the tab title and, when allowed, in a browser
    notification
  kind: product
  entities:
  - entity: captcha
    effect: creates
    facts:
    - Kind
    - Hoster
    - Hoster page
    - Time left
  contexts:
    web:
      place: haul-web::signed-in
---

# Ask for a captcha

## Trigger

A free download meets a captcha.

## Outcome

The download shows Waiting for captcha until the user solves it or ten minutes pass.

## Edge cases

- A hoster that asks for the text in a picture gets an image captcha in the banner instead.
