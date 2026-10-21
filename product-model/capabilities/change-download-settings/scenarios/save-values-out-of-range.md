---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User saves a slot count, Connections per file or Retries beyond what Haul allows
  kind: actor
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - Parallel downloads
    - Connections per file
    - Retries
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The Product keeps each value within its range and shows the values it kept
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - Parallel downloads
    - Connections per file
    - Retries
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Save values out of range

## Trigger

A value is too high or too low.

## Outcome

Parallel downloads lies between 1 and 20, Connections per file between 1 and 16 and Retries at most 50.
