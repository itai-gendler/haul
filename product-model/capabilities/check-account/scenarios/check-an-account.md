---
kind: primary
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
    - Traffic left
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product has the hoster plugin log in with the account
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
- text: The hoster accepts it; the Product shows the fresh type, expiry date, traffic left and check time
  kind: product
  actor: user
  entities:
  - entity: account
    effect: changes
    from: Checking
    to: Valid
    facts:
    - Premium
    - Valid until
    - Traffic left
    - Last checked
    - Hoster session
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
---

# Check an account

## Trigger

The user wants to see how much traffic is left.

## Outcome

The account shows current numbers.
