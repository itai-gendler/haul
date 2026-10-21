---
entities:
- entity: download
  collects:
  - Link
references:
- kind: code
  role: implementation
  target: extension/src/popup.ts
- kind: code
  role: implementation
  target: extension/static/popup.html
---

# Popup

The toolbar popup: how many downloads are active and queued, a field to paste links, sending the
current page, opening Haul and the extension's settings.
