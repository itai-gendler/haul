---
kind: edge
routes:
  web: Haul web
steps:
- text: Ten minutes pass without an answer to a captcha
  kind: condition
  unattended: true
  entities:
  - entity: captcha
    effect: reads
    facts:
    - Time left
  contexts:
    web:
      place: haul-web::signed-in
- text: The Product removes the captcha and queues the download to try again in 30 minutes
  kind: product
  entities:
  - entity: captcha
    effect: removes
  - entity: download
    effect: changes
    from: Connecting
    to: Waiting
    facts:
    - Next try
    - Error
  contexts:
    web:
      place: haul-web::signed-in
---

# Leave a captcha unanswered

## Trigger

The user is away while a captcha waits.

## Outcome

The download tries again later and nothing fails.

## Edge cases

- An image captcha left unanswered ends the same way.
