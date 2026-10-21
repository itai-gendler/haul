---
availability:
- place: haul-web::signed-in
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#extract_archive
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#remember_archive_password
- kind: code
  role: implementation
  target: ui/src/components/Captchas.tsx#AnswerRow
- kind: doc
  role: intent
  target: docs/extraction.md#archive-passwords
---

# Enter archive password

The user answers the banner's question for the password of an archive none of the known passwords opened. A password that opens it joins the top of the archive passwords.
