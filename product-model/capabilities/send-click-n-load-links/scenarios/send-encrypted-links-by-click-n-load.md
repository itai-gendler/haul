---
kind: alternate
routes:
  cnl: Click'n'Load
steps:
- text: The Link site posts encrypted links together with the key snippet
  kind: actor
  actor: link-site
  entities: []
  contexts:
    cnl:
      place: click-n-load
- text: The Product works out the key and decrypts the links
  kind: product
  actor: link-site
  entities: []
  contexts:
    cnl:
      place: click-n-load
- text: The Product puts them in a new package in the link grabber and answers success
  kind: product
  actor: link-site
  entities:
  - entity: package
    effect: creates
    to: In the link grabber
    facts:
    - Name
    - Target folder
    - Source
    - Source page
  - entity: download
    effect: creates
    to: In the link grabber
    facts:
    - Link
    - File name
    - Hoster
    - Online status
    with: package
  contexts:
    cnl:
      place: click-n-load
---

# Send encrypted links by Click'n'Load

## Trigger

The link site protects its links.

## Outcome

The decrypted links wait in the link grabber.

## Edge cases

- A payload that cannot be decrypted is answered with failed and the reason; nothing is added.
