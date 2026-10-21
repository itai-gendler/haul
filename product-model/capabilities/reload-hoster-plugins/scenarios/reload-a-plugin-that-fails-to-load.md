---
kind: edge
routes:
  web: Haul web
steps:
- text: The User chooses Reload
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
- text: The Product loads the other plugins and lists the file that failed with its error
  kind: product
  actor: user
  entities:
  - entity: hoster-plugin
    effect: reads
    facts:
    - File
  contexts:
    web:
      place: haul-web::signed-in::accounts-and-plugins
---

# Reload a plugin that fails to load

## Trigger

A custom plugin file is broken.

## Outcome

The working plugins are loaded; the broken file is named with the reason.
