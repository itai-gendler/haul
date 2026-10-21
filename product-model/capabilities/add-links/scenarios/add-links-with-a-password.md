---
kind: alternate
routes:
  web: Haul web
steps:
- text: The User pastes links and enters the Password from the page that listed them
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product keeps it as the links' download password and as the first of the package's passwords
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
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product checks the links online
  kind: product
  actor: user
  entities:
  - entity: download
    effect: changes
    facts:
    - Online status
    - File name
    - Size
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Add links with a password

## Trigger

The links' page names a password for the files and their archives.

## Outcome

The package shows with password; protected downloads and archives try that password first.
