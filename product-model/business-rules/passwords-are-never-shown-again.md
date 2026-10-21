---
appliesTo:
- type: capability
  id: add-account
- type: capability
  id: change-account-login
- type: capability
  id: add-links
references:
- kind: code
  role: implementation
  target: crates/haul/src/crypto.rs
- kind: code
  role: implementation
  target: crates/haul/src/db.rs#Account
- kind: doc
  role: intent
  target: docs/installation.md#environment-variables
---

# Saved passwords are never shown again

Account passwords, keys and cookies are stored encrypted with the server's secret, and download passwords are kept with their download; neither is shown in the interface after saving. Stored account passwords open only with the secret they were saved with.
