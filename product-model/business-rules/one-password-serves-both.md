---
appliesTo:
- type: capability
  id: add-links
- type: capability
  id: send-click-n-load-links
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#add_links
- kind: code
  role: implementation
  target: crates/haul/src/cnl.rs#submit
---

# One password serves the download and the archives

A password given with the links is kept as the download password of every link and as the package's first archive password, unless separate ones are given. From Click'n'Load the first of the site's passwords is the download password and all of them are archive passwords.
