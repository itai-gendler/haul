---
kind: edge
routes:
  web: Haul web
steps:
- text: Ten minutes pass without an answer
  kind: condition
  unattended: true
  entities:
  - entity: password-question
    effect: reads
    facts:
    - Time left
  contexts:
    web:
      place: haul-web::signed-in
- text: The Product removes the question and queues the download to ask again in 30 minutes
  kind: product
  entities:
  - entity: password-question
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

# Leave the download password unanswered

## Trigger

The user is away.

## Outcome

The download waits and asks again later; nothing fails.
