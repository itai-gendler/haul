---
availability:
- place: haul-web::signed-in
domain: login
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#change_password
- kind: code
  role: implementation
  target: ui/src/routes/Settings.tsx#Password
---

# Change password

The user changes the login password under Settings → Login.
