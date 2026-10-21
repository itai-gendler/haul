---
availability:
- place: haul-web::signed-in
references:
- kind: code
  role: implementation
  target: crates/haul/src/captcha.rs#cancel
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#cancel_captcha
- kind: code
  role: implementation
  target: crates/haul/src/plugins/prelude.js
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#extract_archive
- kind: code
  role: implementation
  target: ui/src/components/Captchas.tsx#CaptchaBanner
---

# Cancel question

The user cancels a captcha, a password question or an archive password question in the banner instead of answering it.
