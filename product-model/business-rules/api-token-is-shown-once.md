---
appliesTo:
- type: capability
  id: create-api-token
- type: capability
  id: send-links-to-haul
- type: capability
  id: test-extension-connection
- type: entity
  id: settings
  facts:
  - API token
references:
- kind: code
  role: implementation
  target: crates/haul/src/auth.rs#rotate_token
---

# An API token is shown once and replaces the previous one

Haul keeps only a fingerprint of the API token, so it is shown once when created; creating a new one makes the old one stop working.
