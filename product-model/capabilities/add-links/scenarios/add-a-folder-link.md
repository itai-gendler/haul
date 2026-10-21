---
kind: alternate
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
    as: folder-link
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
- text: The Product asks the hoster plugin for the files behind the link, with an account where the plugin needs
    one
  kind: product
  actor: user
  entities:
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
  - entity: account
    effect: reads
    facts:
    - Active
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product replaces the link with one download per file, each with its subfolder, size, checksum and the
    folder's password, and names the package after the folder unless the User named it
  kind: product
  actor: user
  entities:
  - entity: download
    as: folder-link
    effect: removes
    from: Reading folder
  - entity: download
    as: file-link
    effect: creates
    to: In the link grabber
    facts:
    - Link
    - File name
    - Hoster
    - Online status
    - Size
    - Checksum
    - Subfolder
    - Download password
  - entity: package
    effect: changes
    facts:
    - Name
    - Target folder
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Add a folder link

## Trigger

The user has a link to a shared folder rather than to single files.

## Outcome

The link grabber shows the folder's files, with their subfolders, in a package named after the folder.

## Edge cases

- Adding never waits for the folder to be read; the link shows Reading folder meanwhile.
- A package started while its folder is still being read queues the files as soon as they are known.
- A package name or target folder the user changed meanwhile is kept.
- A folder with no files keeps the link with an error saying so.
