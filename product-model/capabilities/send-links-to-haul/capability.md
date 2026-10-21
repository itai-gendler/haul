---
availability:
- place: browser-extension
references:
- kind: code
  role: implementation
  target: extension/src/background.ts#send
- kind: code
  role: implementation
  target: extension/src/api.ts#sendLinks
- kind: code
  role: implementation
  target: extension/src/popup.ts
- kind: doc
  role: intent
  target: docs/browser-extension.md
---

# Send links to Haul

From the browser extension the user sends a link, the links in a selection, the current page or pasted links to Haul. They land in the link grabber with the page they came from, unless the extension is set to start them right away.
