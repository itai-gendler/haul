---
availability:
- place: haul-web::signed-in
domain: click-n-load-from-the-desktop
references:
- kind: code
  role: implementation
  target: ui/src/routes/Settings.tsx#checkCnl
- kind: code
  role: implementation
  target: crates/haul/src/cnl.rs#jdcheck
---

# Test Click'n'Load

The user checks from this browser who answers Click'n'Load: the browser extension, Haul on this machine, the desktop forwarder or nothing.
