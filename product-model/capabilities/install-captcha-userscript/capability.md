---
availability:
- place: haul-web::signed-in
domain: captchas
references:
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#captcha_userscript
- kind: code
  role: implementation
  target: ui/src/routes/Settings.tsx#Captchas
- kind: doc
  role: intent
  target: docs/captchas.md#the-userscript
---

# Install captcha userscript

The user installs the captcha userscript from Settings → Captchas into the browser's userscript manager.
