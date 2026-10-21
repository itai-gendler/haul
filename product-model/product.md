---
id: haul
summary: 'A self-hosted download manager for file hosters: paste links or send them with Click''n''Load, and the
  server downloads, verifies, extracts and sorts them while the browser shows it live.'
category: download-manager
tags:
- downloads
- self-hosted
- file-hosters
- click-n-load
authors:
- name: Tristan Teufel
  url: https://github.com/firsttris
license: AGPL-3.0-only
languages:
- en
- de
limitations:
- Haul has one login; there are no other users or roles.
- Hosters are reached only through their hoster plugins or as direct HTTP(S) links; what a hoster allows is up to
  the hoster.
- Captchas that only work on the hoster's own page are solved by the user in their own browser.
- Links sent by Click'n'Load always wait in the link grabber until the user starts them.
- The Done view reaches only the done folder.
references:
- kind: doc
  role: intent
  target: README.md
- kind: doc
  role: context
  target: docs/architecture.md
- kind: doc
  role: intent
  target: docs/hosters.md
- kind: code
  role: implementation
  target: crates/haul/src/main.rs
---

# Haul

Haul is a self-hosted download manager for file hosters that runs on a home server or NAS and is used
from the browser. The user pastes links into the link grabber or sends them from the browser extension
or a site's Click'n'Load button. Haul checks them, groups them in packages, downloads them through
hoster plugins with the user's premium accounts, verifies checksums, extracts the archives and sorts the
files into the done folder, while the browser shows every step live. When a hoster asks for a captcha
or a password, Haul hands the question to the user.

## Intent

"Paste links or send them with Click'n'Load. Your server downloads, extracts and sorts them, your
browser shows it live." Haul is "headless from the start", with "an embedded web UI, no desktop" and "no
account in someone's cloud", and with "hoster plugins you can fix yourself".
