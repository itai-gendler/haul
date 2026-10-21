---
kind: primary
routes:
  web: Haul web
steps:
- text: The User pastes text with links into Paste links, optionally with a name and where its files go, and chooses
    Add
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product keeps each http(s) link once and puts them in a new package in the link grabber, named after
    the links' names unless the User named it
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
    to: In the link grabber
    facts:
    - Link
    - File name
    - Hoster
    - Online status
    with: package
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product checks the links online and fills in name, size and checksum where the hoster tells them
  kind: product
  actor: user
  entities:
  - entity: download
    effect: changes
    facts:
    - Online status
    - File name
    - Size
    - Checksum
    - Error
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Add links to the link grabber

## Trigger

The user has links from a web page or a message.

## Outcome

The package waits in the link grabber with its links checked; nothing downloads yet.

## Edge cases

- A link no hoster plugin claims is kept as a direct link.
- Links of a part set such as Movie.part1.rar and Movie.part2.rar name the package Movie; mixed files name it after the first file and how many follow.
