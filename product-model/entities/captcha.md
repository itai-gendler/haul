---
references:
- kind: code
  role: implementation
  target: crates/haul/src/captcha.rs#CaptchaRequest
- kind: code
  role: implementation
  target: crates/haul/src/captcha.rs#Captchas
- kind: doc
  role: intent
  target: docs/captchas.md
---

# Captcha

A captcha widget a hoster showed that only works on the hoster's own page. It waits in the banner for
the user to solve it in their browser.

## Information kept

- **Kind** — which captcha widget the hoster uses
- **Hoster** — the hoster and its plugin
- **Hoster page** — the page the captcha belongs to
- **Time left** — minutes until it counts as unanswered
