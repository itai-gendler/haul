---
entities:
- entity: extension-settings
  shows:
  - Haul address
  - API token
  - Handle Click'n'Load buttons
  - Start sent links right away
  collects:
  - Haul address
  - API token
  - Handle Click'n'Load buttons
  - Start sent links right away
references:
- kind: code
  role: implementation
  target: extension/src/options.ts
- kind: code
  role: implementation
  target: extension/static/options.html
---

# Haul settings

The extension's options: the connection to Haul and how sent links and Click'n'Load buttons are handled.
