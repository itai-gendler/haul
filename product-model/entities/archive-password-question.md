---
references:
- kind: code
  role: implementation
  target: crates/haul/src/captcha.rs#ask_archive_password
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#extract_archive
- kind: doc
  role: intent
  target: docs/extraction.md#archive-passwords
---

# Archive password question

The question for the password of an archive none of the known passwords opened.

## Information kept

- **Archive name** — the archive to open
- **Package name** — the package it belongs to, when it has one
- **Wrong before** — whether the last answer did not open it
- **Time left** — minutes until it counts as unanswered
