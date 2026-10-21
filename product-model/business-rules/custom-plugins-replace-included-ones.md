---
appliesTo:
- type: capability
  id: reload-hoster-plugins
- type: entity
  id: hoster-plugin
  facts:
  - Origin
  - Replaces
references:
- kind: code
  role: implementation
  target: crates/haul/src/plugins/mod.rs#reload
---

# A custom plugin replaces the included plugin with the same id

Plugins in the custom plugins folder load after the included ones and win over a plugin with the same id; the list says when the included one is newer.
