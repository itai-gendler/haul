---
availability:
- place: haul-web::signed-in
domain: login
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#logout
- kind: code
  role: implementation
  target: ui/src/routes/Settings.tsx#Password
---

# Log out

The user ends the login in this browser from Settings → Login.
