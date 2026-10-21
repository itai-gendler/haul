---
appliesTo:
- type: capability
  id: download-file
- type: capability
  id: resume-download
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#record_failure
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#resume
---

# Failed attempts are retried with a growing pause until Retries run out

After a failed attempt the download waits 10 seconds, doubling with each attempt up to 10 minutes. Once the attempts exceed Retries it fails. Resuming a download counts its attempts from zero.
