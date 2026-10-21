---
kind: primary
result: achieved
routes:
  web: Haul web
steps:
- text: The User pastes links, turns on Start right away, skip the link grabber, and chooses Add
  kind: actor
  actor: user
  capability: add-links
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product queues them in a new package in the downloads
  kind: product
  actor: user
  capability: add-links
  entities:
  - entity: package
    effect: creates
    to: In the downloads
    facts:
    - Name
    - Target folder
    - Source
  - entity: download
    effect: creates
    to: Waiting
    facts:
    - Link
    - File name
    - Hoster
    - Online status
    with: package
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product opens the downloads
  kind: product
  actor: user
  capability: add-links
  entities:
  - entity: download
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The User follows the new downloads as they start
  kind: actor
  actor: user
  capability: browse-downloads
  entities:
  - entity: download
    effect: reads
    facts:
    - File name
    - Progress
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Paste links and watch them download

## Trigger

The user has links that should download now.

## Outcome

The new downloads run and the user watches them.
