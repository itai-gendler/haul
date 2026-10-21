---
appliesTo:
- type: capability
  id: change-language
- type: capability
  id: send-links-to-haul
- type: capability
  id: solve-captcha
references:
- kind: code
  role: implementation
  target: crates/haul/src/i18n.rs
- kind: code
  role: implementation
  target: ui/src/i18n.ts
---

# Every text shows in the chosen language

The web interface and the captcha userscript show German or English as picked in this browser, and messages from the server and the hoster plugins follow, stored errors included; the extension follows the browser's own language.
