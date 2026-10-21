---
actors:
- user
references:
- kind: code
  role: implementation
  target: extension/src/background.ts#send
- kind: code
  role: implementation
  target: extension/src/options.ts
---

# Set up the extension on first use

## Goal

Send a first link from the browser to Haul with a freshly installed extension.

## Success criterion

The link arrives in Haul's link grabber.
