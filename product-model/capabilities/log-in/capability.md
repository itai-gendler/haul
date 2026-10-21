---
availability:
- place: haul-web::signed-out
domain: login
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#login
- kind: code
  role: implementation
  target: ui/src/routes/Login.tsx#Login
---

# Log in

The user logs in with the user name and password of Haul's one login.
