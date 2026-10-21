---
availability:
- place: haul-web::signed-in
references:
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#update_settings
- kind: code
  role: implementation
  target: crates/haul/src/db.rs#Settings
- kind: code
  role: implementation
  target: ui/src/routes/Settings.tsx#SettingsPage
---

# Change download settings

The user changes the settings under Settings → Downloads: parallel downloads, connections per file, the bandwidth limit, retries, and what happens after the download and the extraction.
