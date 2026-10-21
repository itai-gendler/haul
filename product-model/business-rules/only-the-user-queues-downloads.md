---
appliesTo:
- type: entity
  id: download
  effect: creates
  to: Waiting
permits:
- actors:
  - user
- unattended: true
references:
- kind: code
  role: implementation
  target: crates/haul/src/cnl.rs#submit
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#crawl_package
---

# Only the user queues downloads

Links from link sites arrive in the link grabber and wait there; only the user, through the web interface, the browser extension or starting a package, puts downloads in the queue. A folder read for a package the user already started queues its files for the user.
