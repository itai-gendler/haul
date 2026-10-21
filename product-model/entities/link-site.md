---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: crates/haul/src/cnl.rs#router
- kind: doc
  role: intent
  target: docs/click-n-load.md
---

# Link site

A web page with a Click'n'Load button that sends its links to the download manager on the user's
computer. Haul accepts these links and keeps them in the link grabber.
