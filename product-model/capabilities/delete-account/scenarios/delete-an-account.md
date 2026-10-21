---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Delete account on an account
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts:
    - Hoster
    - User
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product deletes the account and its saved session
  kind: product
  actor: user
  entities:
  - entity: account
    effect: removes
    from: Valid
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
---

# Delete an account

## Trigger

The account is closed or no longer wanted.

## Outcome

The account is gone; its hoster's downloads run without it.
