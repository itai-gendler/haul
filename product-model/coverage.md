---
scope: The Haul server, its web interface, the browser extension, the Click'n'Load forwarder, the captcha userscript
  and the plugin contract.
method: Static reading of the tracked source and documentation at the pinned commit.
covered:
- description: Server API, login, queue, workers, extraction, checksums, captchas and the Done view.
  paths:
  - crates/haul/src/api.rs
  - crates/haul/src/auth.rs
  - crates/haul/src/engine/
  - crates/haul/src/captcha.rs
  - crates/haul/src/captcha.user.js
  - crates/haul/src/files.rs
  - crates/haul/src/db.rs
  - crates/haul/src/events.rs
  - crates/haul/src/main.rs
  - crates/haul/src/config.rs
  - crates/haul/migrations/
- description: Click'n'Load listener and the desktop forwarder.
  paths:
  - crates/haul/src/cnl.rs
  - crates/haul-cnl/
- description: Plugin host and the contract every hoster plugin follows.
  paths:
  - crates/haul/src/plugins/
  - packages/plugin-sdk/src/index.ts
- description: Web interface pages, banner and live updates.
  paths:
  - ui/src/
- description: Browser extension background, popup, options and Click'n'Load relay.
  paths:
  - extension/src/
  - extension/static/
- description: Server and interface message texts in both languages.
  paths:
  - crates/haul/src/i18n.rs
  - ui/messages/
  - extension/_locales/
exclusions:
- description: Build, release, image and CI machinery.
  paths:
  - .github/
  - docker/
  - scripts/
  - crates/haul/build.rs
  - extension/build.mjs
  - crates/haul/src/ui.rs
- description: 'Developer tooling for writing hoster plugins: the agent skill and the plugin test helpers.'
  paths:
  - .claude/skills/hoster-plugin/
  - packages/plugin-sdk/src/testing.ts
- description: Documentation site configuration, styling and images.
  paths:
  - mkdocs.yml
  - docs/assets/
  - ui/src/styles.css
  - ui/src/components/icons.tsx
  - extension/icons/
  - ui/public/
unmapped:
- description: 'Per-hoster plugin code: how each hoster''s pages, waits, captchas and accounts are handled.'
  paths:
  - plugins/
  - packages/plugin-sdk/src/xfs.ts
- description: The probe command that tries plugins against real hosters.
  paths:
  - crates/haul/src/probe.rs
limitations: []
---

# Coverage
