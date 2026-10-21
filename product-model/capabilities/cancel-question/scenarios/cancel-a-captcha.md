---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Cancel next to a waiting captcha
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
- text: The Product removes the captcha and marks the download failed with captcha cancelled
  kind: product
  actor: user
  entities:
  - entity: captcha
    effect: removes
  - entity: download
    effect: changes
    from: Connecting
    to: Failed
    facts:
    - Error
  contexts:
    web:
      place: haul-web::signed-in
---

# Cancel a captcha

## Trigger

The user does not want to solve the captcha.

## Outcome

The download fails at once; resuming it asks again.

## Edge cases

- Cancelling an image captcha ends the download the same way.
