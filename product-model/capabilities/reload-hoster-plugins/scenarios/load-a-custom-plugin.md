---
kind: primary
routes:
  web: Haul web
steps:
- text: A custom plugin file is in the custom plugins folder
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Custom plugins folder
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The User chooses Reload under Plugins
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product loads every plugin again; the custom one is listed as Custom file and replaces the included
    plugin with the same id
  kind: product
  actor: user
  entities:
  - entity: hoster-plugin
    effect: creates
    facts:
    - Name
    - Version
    - Domains
    - Link patterns
    - Origin
    - File
    - Needs an account
    - Account form
    - Replaces
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
---

# Load a custom plugin

## Trigger

The user wrote or fixed a plugin for a hoster.

## Outcome

Links of that hoster are handled by the custom plugin, without a new image or a restart.
