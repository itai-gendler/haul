---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User pastes links, turns on Start right away, skip the link grabber, and chooses Add
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product puts them in a new package that goes straight to the downloads, its links queued
  kind: product
  actor: user
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
  entities:
  - entity: download
    effect: reads
    facts: []
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Add links and start right away

## Trigger

The user trusts the links and wants them downloading now.

## Outcome

The links are queued without an online check, and the user sees the downloads.
