---
availability:
- place: haul-web::signed-in
domain: click-n-load-from-the-desktop
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#rotate_token
- kind: code
  role: implementation
  target: ui/src/routes/Settings.tsx#ApiToken
---

# Create API token

The user creates the API token the browser extension and the desktop forwarder use, under Settings → Click'n'Load from the desktop. A new token replaces the old one.
