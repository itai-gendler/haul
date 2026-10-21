---
availability:
- place: haul-web::signed-in
references:
- kind: code
  role: implementation
  target: ui/src/components/Captchas.tsx#AnswerRow
- kind: code
  role: implementation
  target: crates/haul/src/captcha.rs#solve
- kind: doc
  role: intent
  target: docs/captchas.md
---

# Answer image captcha

The user types the text of an image captcha shown in the banner; no browser extension is needed.
