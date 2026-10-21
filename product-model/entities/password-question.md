---
references:
- kind: code
  role: implementation
  target: crates/haul/src/captcha.rs#ask_password
- kind: code
  role: implementation
  target: crates/haul/src/plugins/host.rs
- kind: doc
  role: intent
  target: docs/hosters.md#password-protected-files
---

# Password question

The question for the password of a protected file or folder, asked in the banner when the download
has none or the hoster rejected it.

## Information kept

- **Download name** — the file or folder the password is for
- **Hoster** — the hoster and its plugin
- **Wrong before** — whether the last password was wrong
- **Time left** — minutes until it counts as unanswered
