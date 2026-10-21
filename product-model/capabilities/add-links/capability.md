---
availability:
- place: haul-web::signed-in
domain: link-grabber
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#add_links
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#parse_links
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#crawl_package
- kind: code
  role: implementation
  target: ui/src/routes/Collector.tsx#AddLinksForm
- kind: doc
  role: intent
  target: docs/architecture.md#folder-links
---

# Add links

The user pastes text with links into the link grabber. Haul keeps every http(s) link once, groups them in one package and checks them online, or queues them at once when asked to. Folder links are read into their files in the background.
