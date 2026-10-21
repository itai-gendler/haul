---
kind: validation
routes:
  web: Haul web
steps:
- text: A download of a hoster whose plugin needs an account reaches the front of the queue
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts:
    - Hoster
  - entity: hoster-plugin
    effect: reads
    facts:
    - Needs an account
  - entity: account
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product takes it from the queue and looks for an active account of that hoster
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Waiting
    to: Connecting
    facts: []
  - entity: account
    effect: reads
    facts:
    - Active
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: No active account of that hoster is usable
  kind: condition
  entities:
  - entity: account
    effect: reads
    facts:
    - Active
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product marks the download failed, saying the hoster needs an account
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Connecting
    to: Failed
    facts:
    - Error
  - entity: account
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Fail without an account

## Trigger

A link of a premium-only hoster is started without an account.

## Outcome

The download fails without being tried; adding an account and resuming it starts it.
