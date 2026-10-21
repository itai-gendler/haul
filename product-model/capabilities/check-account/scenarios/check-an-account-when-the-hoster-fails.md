---
kind: edge
routes:
  web: Haul web
steps:
- text: The User chooses Check on an account
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts:
    - Hoster
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product has the hoster plugin log in, and the hoster cannot be reached
  kind: product
  actor: user
  entities:
  - entity: account
    effect: changes
    from: Valid
    to: Checking
    facts: []
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product shows the account Error with the message
  kind: product
  actor: user
  entities:
  - entity: account
    effect: changes
    from: Checking
    to: Error
    facts:
    - Error
    - Last checked
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
---

# Check an account when the hoster fails

## Trigger

The hoster is down during the check.

## Outcome

The account shows Error; unlike Invalid, downloads still try it.
