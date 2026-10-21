---
kind: edge
routes:
  web: Haul web
steps:
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
- text: The Product opens the hoster's page with the captcha task
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
- text: The userscript is not installed or not allowed to run in this browser
  kind: condition
  entities: []
  contexts:
    web:
      place: captcha-userscript::captcha-page
- text: The hoster's full page shows and no answer reaches the Product; the captcha keeps waiting
  kind: product
  actor: user
  entities:
  - entity: captcha
    effect: reads
    facts:
    - Time left
  contexts:
    web:
      place: haul-web::signed-in
---

# Open a captcha without the userscript

## Trigger

The browser has no working userscript.

## Outcome

The captcha waits until its time runs out; the banner links to Set up the userscript.
