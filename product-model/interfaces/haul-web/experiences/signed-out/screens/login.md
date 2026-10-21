---
entities:
- entity: user
  collects:
  - User name
  - Password
references:
- kind: code
  role: implementation
  target: ui/src/routes/Login.tsx#Login
---

# Login

The first visit asks to create the user for the web interface; later visits ask to log in.
