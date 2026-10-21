---
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs
---

# Login

Creating the one login, logging in and out, and changing the password.

## Boundary

It does not own the API token the browser extension and the desktop forwarder use.
