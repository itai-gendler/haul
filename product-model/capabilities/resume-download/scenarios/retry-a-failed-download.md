---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User chooses Resume on a failed download
  kind: actor
  actor: user
  entities:
  - entity: download
    effect: reads
    facts:
    - File name
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product clears the error and puts it back in the queue with its retries counted from zero
  kind: product
  actor: user
  entities:
  - entity: download
    effect: changes
    from: Failed
    to: Waiting
    facts:
    - Attempts
    - Next try
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Retry a failed download

## Trigger

The cause of a failure is fixed, such as a new account or a hoster that is back.

## Outcome

The download is tried again with the full number of retries.
