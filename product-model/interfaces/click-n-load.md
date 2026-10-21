---
type: api
actors:
- link-site
references:
- kind: code
  role: implementation
  target: crates/haul/src/cnl.rs#router
- kind: code
  role: implementation
  target: crates/haul-cnl/src/main.rs
- kind: code
  role: implementation
  target: extension/src/cnl-page.ts
- kind: doc
  role: intent
  target: docs/click-n-load.md
---

# Click'n'Load

The Click'n'Load contract link sites use: plain or encrypted links posted to `127.0.0.1:9666` on the
computer with the browser. Haul answers there itself on its own machine; on a server, the browser
extension or the desktop forwarder take the request on the desktop and pass it to Haul with the API
token.
