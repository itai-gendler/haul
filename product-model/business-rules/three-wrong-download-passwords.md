---
appliesTo:
- type: capability
  id: enter-download-password
- type: entity
  id: download
  facts:
  - Download password
references:
- kind: code
  role: implementation
  target: packages/plugin-sdk/src/index.ts#withPassword
---

# Three wrong download passwords fail the download

After a password the hoster rejects, the user is asked again; after the third wrong one the download fails and the password is forgotten.
