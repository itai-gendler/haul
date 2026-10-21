---
kind: primary
routes:
  web: Haul web
steps:
- text: The User turns off Active for an account
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts:
    - Hoster
    - Active
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product keeps the account but no longer picks it
  kind: product
  actor: user
  entities:
  - entity: account
    effect: changes
    facts:
    - Active
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
---

# Deactivate an account

## Trigger

The user wants to save an account's traffic or test free downloads.

## Outcome

Downloads of that hoster run without this account.
