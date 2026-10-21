---
availability:
- place: haul-web::signed-in
domain: captchas
references:
- kind: code
  role: implementation
  target: ui/src/routes/Settings.tsx#Captchas
- kind: code
  role: implementation
  target: ui/src/components/Captchas.tsx#CaptchaBanner
---

# Allow captcha notifications

The user allows browser notifications under Settings → Captchas, so a waiting captcha or password is noticed while Haul is in the background.
