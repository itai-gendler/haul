---
kind: primary
routes:
  web: Haul web
steps:
- text: The User opens the downloads
  kind: actor
  actor: user
  entities:
  - entity: package
    effect: reads
    facts:
    - Name
  - entity: download
    effect: reads
    facts:
    - File name
    - Hoster
    - Size
    - Progress
    - Error
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product lists each started package with its downloads, their progress, speed and time left, and updates
    them about once a second
  kind: product
  actor: user
  entities:
  - entity: package
    effect: reads
    facts:
    - Name
    - Extraction error
  - entity: download
    effect: reads
    facts:
    - File name
    - Hoster
    - Size
    - Progress
    - Error
    - Next try
    - Checksum result
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product shows active downloads against Parallel downloads, the queue, what finished today, the premium
    traffic left and the free disk space
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - Parallel downloads
    - Bandwidth limit
  - entity: account
    effect: reads
    facts:
    - Premium
    - Traffic left
  - entity: download
    effect: reads
    facts:
    - Finished at
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Follow the downloads

## Trigger

The user wants to see how the downloads are doing.

## Outcome

The user sees every started download and the totals, current without reloading.

## Edge cases

- A download waiting for its next try shows Retrying in with the time left and the reason.
- A download whose hoster asked for a captcha or password shows Waiting for captcha or Waiting for password.
- When the live connection drops, the sidebar shows Disconnected.
