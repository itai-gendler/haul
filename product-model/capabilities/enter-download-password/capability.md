---
availability:
- place: haul-web::signed-in
references:
- kind: code
  role: implementation
  target: crates/haul/src/captcha.rs#ask_password
- kind: code
  role: implementation
  target: ui/src/components/Captchas.tsx#AnswerRow
- kind: code
  role: implementation
  target: packages/plugin-sdk/src/index.ts#withPassword
- kind: doc
  role: intent
  target: docs/hosters.md#password-protected-files
---

# Enter download password

The user answers the banner's question for the password of a protected file or folder. Haul keeps the password with the download and asks again when the hoster rejects it.
