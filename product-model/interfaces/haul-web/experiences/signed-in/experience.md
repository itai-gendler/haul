---
actors:
- user
access: authenticated
references:
- kind: code
  role: implementation
  target: ui/src/components/Layout.tsx#Layout
- kind: code
  role: implementation
  target: ui/src/components/Captchas.tsx#CaptchaBanner
---

# Signed in

The signed-in user works with the link grabber, the downloads, the done folder, accounts and plugins,
and settings. Captchas and password questions appear in a banner at the top of every page, in the tab
title and, if allowed, as browser notifications.
