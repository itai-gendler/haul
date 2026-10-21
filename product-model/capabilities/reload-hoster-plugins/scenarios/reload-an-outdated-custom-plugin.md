---
kind: alternate
routes:
  web: Haul web
steps:
- text: A custom plugin replaces an included plugin whose version is higher
  kind: condition
  entities:
  - entity: hoster-plugin
    effect: reads
    facts:
    - Version
    - Replaces
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The User chooses Reload
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product loads it and warns that the custom file hides a newer included plugin, until the file is deleted
    and plugins are reloaded
  kind: product
  actor: user
  entities:
  - entity: hoster-plugin
    effect: changes
    facts:
    - Replaces
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
---

# Reload an outdated custom plugin

## Trigger

Haul was updated after the user copied a plugin.

## Outcome

The list shows Outdated on the custom plugin.
