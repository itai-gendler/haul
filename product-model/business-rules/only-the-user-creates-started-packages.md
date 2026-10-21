---
appliesTo:
- type: entity
  id: package
  effect: creates
  to: In the downloads
permits:
- actors:
  - user
references:
- kind: code
  role: implementation
  target: crates/haul/src/cnl.rs#submit
---

# Only the user creates started packages

A package created from a link site's links always starts in the link grabber, whatever the extension's Start sent links right away says.
