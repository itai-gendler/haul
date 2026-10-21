---
availability:
- place: haul-web::signed-in
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#fill_slots
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#execute
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#record_failure
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#pick_account
- kind: doc
  role: intent
  target: docs/architecture.md#errors-retries-and-waits
- kind: doc
  role: intent
  target: docs/architecture.md#segmented-downloads
---

# Download file

Haul works through the queue on its own: in package order it starts as many downloads as Parallel downloads allows, has the hoster plugin get the direct address with the best account, loads the bytes in segments, verifies the checksum and moves the file into the package folder. Hoster waits, limits and failures decide when a download is tried again.
