---
kind: primary
routes:
  web: Haul web
steps:
- text: The User turns on Active for an account
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
- text: The Product picks the account for that hoster again
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

# Activate an account

## Trigger

An account set aside earlier should be used again.

## Outcome

The account takes part in choosing an account again.
