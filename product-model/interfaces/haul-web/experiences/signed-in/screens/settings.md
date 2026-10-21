---
entities:
- entity: settings
  shows:
  - Parallel downloads
  - Connections per file
  - Bandwidth limit
  - Retries
  - Extract finished packages automatically
  - Delete archives after successful extraction
  - Remove the downloads from the list after successful extraction
  - Ask for the archive password when none fits
  - Verify the checksum
  - Archive passwords
  - API token
  - Running downloads folder
  - Finished files folder
  - Custom plugins folder
  - Extractors
  collects:
  - Parallel downloads
  - Connections per file
  - Bandwidth limit
  - Retries
  - Extract finished packages automatically
  - Delete archives after successful extraction
  - Remove the downloads from the list after successful extraction
  - Ask for the archive password when none fits
  - Verify the checksum
  - Archive passwords
- entity: user
  collects:
  - Password
entryPoints:
- haul-web: /einstellungen
references:
- kind: code
  role: implementation
  target: ui/src/routes/Settings.tsx#SettingsPage
---

# Settings

Haul's version, the download settings, the folders and extractors, the archive passwords, the language,
the captcha userscript, Click'n'Load from the desktop with its API token, and the login.
