---
type: web
actors:
- user
references:
- kind: code
  role: implementation
  target: crates/haul/src/captcha.user.js
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#solve_captcha
- kind: doc
  role: intent
  target: docs/captchas.md#the-userscript
---

# Captcha userscript

The userscript the user installs from Settings → Captchas. On a hoster page Haul opened with a captcha
task, it shows only the captcha and sends the answer back to Haul.
