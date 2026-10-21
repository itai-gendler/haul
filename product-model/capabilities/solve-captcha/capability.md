---
availability:
- place: haul-web::signed-in
- place: captcha-userscript
references:
- kind: code
  role: implementation
  target: ui/src/components/Captchas.tsx#CaptchaBanner
- kind: code
  role: implementation
  target: ui/src/components/Captchas.tsx#captchaUrl
- kind: code
  role: implementation
  target: crates/haul/src/captcha.user.js
- kind: code
  role: implementation
  target: crates/haul/src/captcha.rs#solve
- kind: code
  role: implementation
  target: crates/haul/src/plugins/prelude.js
- kind: doc
  role: intent
  target: docs/captchas.md
---

# Solve captcha

The user solves a captcha that only works on the hoster's page in their own browser: Solve opens that page, the captcha userscript shows only the captcha there and sends the answer back, and the download continues.
