---
kind: primary
routes:
  cnl: Click'n'Load
steps:
- text: The Link site posts its links to Click'n'Load
  kind: actor
  actor: link-site
  entities: []
  contexts:
    cnl:
      place: click-n-load
- text: The Product puts them in a new package in the link grabber, named after the package name the site sent or
    Click'n'Load and the site's host, with the page they came from
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
- text: The Product answers success
  kind: product
  actor: link-site
  entities: []
  contexts:
    cnl:
      place: click-n-load
---

# Send links by Click'n'Load

## Trigger

The user presses a Click'n'Load button on a link site.

## Outcome

The links wait in the link grabber with their source page; nothing starts.

## Edge cases

- Folder links among them are read into their files as with pasted links.
