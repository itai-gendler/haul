---
type: web
actors:
- user
entryPoints:
- web: /
references:
- kind: code
  role: implementation
  target: ui/src/main.tsx
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#router
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#require_auth
---

# Haul web

The web interface the server serves: the user signs in and manages links, downloads, the done folder,
accounts and settings, with live progress.
