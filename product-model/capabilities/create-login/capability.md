---
availability:
- place: haul-web::signed-out
domain: login
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#setup
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#ensure_initial_user
- kind: code
  role: implementation
  target: ui/src/routes/Login.tsx#Login
---

# Create the login

On the first visit, before any login exists, Haul asks for a user name and a password and creates its one login. It can also be created from the server's configuration at the first start.
