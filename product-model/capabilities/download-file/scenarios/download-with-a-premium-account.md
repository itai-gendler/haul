---
kind: alternate
routes:
  web: Haul web
steps:
- text: A download of a hoster with an active account reaches the front of the queue
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts:
    - Hoster
  - entity: account
    effect: reads
    facts:
    - Active
    - Traffic left
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product picks that hoster's active account with the most traffic left that the hoster has not rejected,
    and has the plugin log in with its saved session
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
    - Traffic left
    - Hoster session
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product keeps the account's hoster session for the next call
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Hoster session
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product loads the bytes over as many connections as Connections per file and the hoster allow
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Connecting
    to: Downloading
    facts:
    - File name
    - Size
    - Progress
  - entity: settings
    effect: reads
    facts:
    - Connections per file
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product moves the finished file into the package folder
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Downloading
    to: Finished
    facts:
    - File name
    - Finished at
  - entity: file
    effect: creates
    facts:
    - Name
    - Path
    - Size
    - Modified
  - entity: package
    effect: reads
    facts:
    - Target folder
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Download with a premium account

## Trigger

The user has a premium account for the hoster.

## Outcome

The file downloads with the account, without free waits, and the login is reused next time.
