---
appliesTo:
- type: capability
  id: solve-captcha
- type: capability
  id: answer-image-captcha
- type: capability
  id: enter-download-password
- type: capability
  id: enter-archive-password
- type: capability
  id: cancel-question
references:
- kind: code
  role: implementation
  target: crates/haul/src/captcha.rs#TIMEOUT
- kind: code
  role: implementation
  target: crates/haul/src/plugins/prelude.js
---

# A captcha or password question waits ten minutes

Each captcha, image captcha and password question waits ten minutes for an answer and then counts as unanswered. An unanswered captcha or download password lets the download try again 30 minutes later; cancelling one fails the download at once.
