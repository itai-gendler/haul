---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Change login on an Invalid account, enters the new password and chooses Save and check
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts:
    - Hoster
    - User
    - Error
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product stores it encrypted, drops the saved hoster session and checks the account again
  kind: product
  actor: user
  entities:
  - entity: account
    effect: changes
    from: Invalid
    to: Checking
    facts:
    - Password
    - Hoster session
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The hoster accepts the login and the account shows Valid
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
    - Error
    - Hoster session
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
---

# Fix a rejected login

## Trigger

The account's password changed at the hoster, or exported cookies expired.

## Outcome

The account is Valid again and downloads use it.
