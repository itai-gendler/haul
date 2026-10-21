---
availability:
- place: haul-web::signed-in
domain: downloads
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#resume
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#resume_all
- kind: code
  role: implementation
  target: ui/src/routes/Downloads.tsx#DownloadsPage
---

# Resume download

The user resumes paused downloads or retries failed ones, one at a time, per package or all at once.
