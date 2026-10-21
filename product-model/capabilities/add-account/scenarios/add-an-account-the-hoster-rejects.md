---
kind: edge
routes:
  web: Haul web
steps:
- text: The User fills in the hoster's form with a wrong password and chooses Add
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
- text: The hoster rejects the login; the Product shows the account Invalid with the hoster's message and no longer
    picks it
  kind: product
  actor: user
  entities:
  - entity: account
    effect: changes
    from: Checking
    to: Invalid
    facts:
    - Error
    - Last checked
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
---

# Add an account the hoster rejects

## Trigger

The user mistyped the account's password.

## Outcome

The account is listed as Invalid with the reason.
