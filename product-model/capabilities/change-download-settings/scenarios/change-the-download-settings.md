---
kind: primary
routes:
  web: Haul web
steps:
- text: The User changes values on the settings page and chooses Save
  kind: actor
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - Parallel downloads
    - Connections per file
    - Bandwidth limit
    - Retries
    - Extract finished packages automatically
    - Delete archives after successful extraction
    - Remove the downloads from the list after successful extraction
    - Ask for the archive password when none fits
    - Verify the checksum
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The Product saves them, applies the bandwidth limit at once and starts more downloads if slots opened
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - Parallel downloads
    - Connections per file
    - Bandwidth limit
    - Retries
    - Extract finished packages automatically
    - Delete archives after successful extraction
    - Remove the downloads from the list after successful extraction
    - Ask for the archive password when none fits
    - Verify the checksum
  - entity: download
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Change the download settings

## Trigger

The user wants Haul to download differently.

## Outcome

The page says Saved and the queue follows the new values.
