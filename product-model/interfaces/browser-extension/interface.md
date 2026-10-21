---
type: web
actors:
- user
references:
- kind: code
  role: implementation
  target: extension/src/background.ts
- kind: code
  role: implementation
  target: extension/src/api.ts
- kind: code
  role: implementation
  target: extension/static/popup.html
- kind: doc
  role: intent
  target: docs/browser-extension.md
---

# Browser extension

The Haul extension for the user's own browser. It sends links to Haul from the right-click menu and its
popup, and takes over Click'n'Load buttons on pages, sending everything to the user's Haul with the
API token.
