---
references:
- kind: code
  role: implementation
  target: crates/haul/src/captcha.rs#CaptchaRequest
- kind: code
  role: implementation
  target: crates/haul/src/plugins/host.rs#fetch_image
- kind: doc
  role: intent
  target: docs/captchas.md
---

# Image captcha

A picture with text a hoster asks to be typed. Haul shows the picture in the banner.

## Information kept

- **Hoster** — the hoster and its plugin
- **Picture** — the picture, loaded with the plugin's session
- **Time left** — minutes until it counts as unanswered
