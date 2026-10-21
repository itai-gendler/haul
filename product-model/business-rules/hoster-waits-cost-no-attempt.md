---
appliesTo:
- type: capability
  id: download-file
- type: capability-scenario
  id: leave-a-captcha-unanswered
- type: capability-scenario
  id: leave-the-download-password-unanswered
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#record_failure
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#apply_hoster_waits
---

# A wait the hoster names never uses up an attempt

Free download limits, countdowns and unanswered captchas or passwords make the download wait until the named time without counting against Retries. A limit for the whole hoster holds every waiting download of that hoster until then.
