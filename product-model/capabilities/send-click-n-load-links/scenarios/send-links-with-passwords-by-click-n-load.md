---
kind: alternate
routes:
  cnl: Click'n'Load
steps:
- text: The Link site posts links together with passwords
  kind: actor
  actor: link-site
  entities: []
  contexts:
    cnl:
      place: click-n-load
- text: The Product keeps the passwords as the package's archive passwords and the first one as the links' download
    password
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
    - Passwords
  - entity: download
    effect: creates
    to: In the link grabber
    facts:
    - Link
    - File name
    - Hoster
    - Online status
    - Download password
    with: package
  contexts:
    cnl:
      place: click-n-load
---

# Send links with passwords by Click'n'Load

## Trigger

The link site knows the archive password.

## Outcome

The package shows with password in the link grabber.
