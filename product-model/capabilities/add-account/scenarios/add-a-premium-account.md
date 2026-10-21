---
kind: primary
routes:
  web: Haul web
steps:
- text: The User picks the hoster, fills in the fields its plugin labels, such as user name and password or an API
    key, and chooses Add
  kind: actor
  actor: user
  entities:
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
    - Account form
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product stores the account active, with the password encrypted
  kind: product
  actor: user
  entities:
  - entity: account
    effect: creates
    to: Unchecked
    facts:
    - Hoster
    - User
    - Password
    - Active
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product has the hoster plugin log in
  kind: product
  actor: user
  entities:
  - entity: account
    effect: changes
    from: Unchecked
    to: Checking
    facts: []
  - entity: hoster-plugin
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The hoster accepts the login; the Product shows the account Valid with its type, expiry date and traffic
    left
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

# Add a premium account

## Trigger

The user has a premium account at a hoster.

## Outcome

The account is listed as Valid, and downloads of that hoster use it.

## Edge cases

- Only hosters whose plugin needs or can check an account are offered.
- A plugin without an account check leaves the account Unchecked; it is still used.
