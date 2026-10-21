---
references:
- kind: code
  role: implementation
  target: extension/src/settings.ts#Settings
- kind: code
  role: implementation
  target: extension/src/options.ts
- kind: doc
  role: intent
  target: docs/browser-extension.md#set-up
---

# Extension settings

What the user sets in the browser extension's options, kept in that browser.

## Information kept

- **Haul address** — the address Haul is opened at in the browser
- **API token** — the token created in Haul under Settings → Click'n'Load from the desktop
- **Handle Click'n'Load buttons** — on by default
- **Start sent links right away** — instead of keeping them in the link grabber; off by default
