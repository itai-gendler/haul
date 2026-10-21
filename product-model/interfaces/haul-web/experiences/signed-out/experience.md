---
actors:
- user
access: public
references:
- kind: code
  role: implementation
  target: ui/src/routes/Login.tsx#Login
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#state
---

# Signed out

Before signing in, the user creates the one login on the first visit or logs in, in German or English.
