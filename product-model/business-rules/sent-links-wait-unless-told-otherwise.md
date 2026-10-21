---
appliesTo:
- type: capability
  id: send-links-to-haul
- type: capability
  id: change-extension-settings
references:
- kind: code
  role: implementation
  target: extension/src/api.ts#sendLinks
- kind: code
  role: implementation
  target: extension/src/background.ts
---

# Links the extension sends wait in the link grabber unless told otherwise

Links sent from the extension go to the link grabber unless Start sent links right away is on; Click'n'Load links go to the link grabber either way, and only while Handle Click'n'Load buttons is on does the extension take them.
