---
kind: primary
routes:
  web: Haul web
steps:
- text: The banner says a captcha is waiting, naming the hoster and the minutes left
  kind: condition
  entities:
  - entity: captcha
    effect: reads
    facts:
    - Hoster
    - Time left
  contexts:
    web:
      place: haul-web::signed-in
- text: The User chooses Solve
  kind: actor
  actor: user
  entities:
  - entity: captcha
    effect: reads
    facts:
    - Hoster
  contexts:
    web:
      place: haul-web::signed-in
- text: 'The Product opens the hoster''s page in a new tab with the captcha task after the # in the address'
  kind: product
  actor: user
  entities:
  - entity: captcha
    effect: reads
    facts:
    - Hoster page
  contexts:
    web:
      place: captcha-userscript::captcha-page
- text: The captcha userscript replaces the page with only the captcha
  kind: product
  actor: user
  entities:
  - entity: captcha
    effect: reads
    facts:
    - Kind
  contexts:
    web:
      place: captcha-userscript::captcha-page
- text: The User solves the captcha on the page
  kind: actor
  actor: user
  entities:
  - entity: captcha
    effect: reads
    facts:
    - Kind
  contexts:
    web:
      place: captcha-userscript::captcha-page
- text: The userscript sends the answer to Haul with the captcha's one-time secret; the Product takes it, removes
    the captcha and the download goes on
  kind: product
  actor: user
  entities:
  - entity: captcha
    effect: removes
  - entity: download
    effect: reads
    facts:
    - File name
  contexts:
    web:
      place: captcha-userscript::captcha-page
- text: The page says it is solved and the tab can be closed
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: captcha-userscript::captcha-page
---

# Solve a captcha in the browser

## Trigger

A hoster asked for a captcha while a download connects.

## Outcome

The download continues by itself; the banner no longer shows the captcha.

## Edge cases

- An answer that comes after the captcha expired or was solved is not accepted, and the page says so.
- Captchas on hoster login pages, such as during an account check, are solved the same way.
