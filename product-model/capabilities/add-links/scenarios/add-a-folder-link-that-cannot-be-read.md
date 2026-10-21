---
kind: edge
routes:
  web: Haul web
steps:
- text: The User pastes a link to a hoster folder and chooses Add
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product puts the link in a new package in the link grabber, marked Reading folder
  kind: product
  actor: user
  entities:
  - entity: package
    effect: creates
    to: In the link grabber
    facts:
    - Name
    - Target folder
    - Source
  - entity: download
    effect: creates
    to: Reading folder
    facts:
    - Link
    - File name
    - Hoster
    - Online status
    with: package
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The hoster plugin cannot list the folder
  kind: condition
  entities:
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product keeps the link in the link grabber with the hoster's error, marked offline when the hoster says
    it is gone
  kind: product
  actor: user
  entities:
  - entity: download
    effect: changes
    from: Reading folder
    to: In the link grabber
    facts:
    - Error
    - Online status
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Add a folder link that cannot be read

## Trigger

The folder is gone or the hoster refuses to list it.

## Outcome

The link stays visible in the link grabber with the reason.
