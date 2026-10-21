---
availability:
- place: haul-web::signed-in
domain: accounts-and-plugins
references:
- kind: code
  role: implementation
  target: crates/haul/src/plugins/mod.rs#reload
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#reload_plugins
- kind: doc
  role: intent
  target: docs/plugins.md#building-and-installing
---

# Reload hoster plugins

The user reloads the hoster plugins after putting custom plugin files into the custom plugins folder. A custom plugin with the same id as an included one replaces it.
