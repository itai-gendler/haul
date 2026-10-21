---
domain: accounts-and-plugins
relations:
- entity: account
  verb: logs in with
  cardinality: one-to-many
- entity: download
  verb: handles
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: crates/haul/src/plugins/mod.rs#Plugin
- kind: code
  role: implementation
  target: crates/haul/src/plugins/mod.rs#PluginManager
- kind: doc
  role: intent
  target: docs/plugins.md
- kind: doc
  role: intent
  target: docs/hosters.md
---

# Hoster plugin

The part of Haul that knows one hoster: which links are its own, how to check them, list a folder,
get a file's direct address and check an account. Plugins come with Haul or are custom files the user
adds.

## Information kept

- **Name** — the hoster's name
- **Version** — the plugin's version
- **Domains** — the hoster's domains, shown as what the plugin supports
- **Link patterns** — the link patterns it claims; the first plugin whose pattern matches handles a link
- **Origin** — Included in Haul or Custom file
- **File** — where the plugin was loaded from
- **Needs an account** — Premium account only, or Works without an account
- **Account form** — the labels and help the plugin gives for its account fields
- **Replaces** — the included plugin a custom file hides, and whether that one is newer
