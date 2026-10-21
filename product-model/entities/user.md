---
kind: person
acts: external
domain: login
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#setup
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#login
- kind: doc
  role: intent
  target: docs/installation.md
---

# User

The person who runs Haul on their server and uses it from the browser, the browser extension and the
captcha userscript. Haul has exactly this one login.

## Information kept

- **User name** — the name the login was created with
- **Password** — the login password, at least 8 characters
