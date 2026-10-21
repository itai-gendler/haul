---
entities:
- entity: package
  shows:
  - Name
  - Target folder
  - Source
  - Source page
  collects:
  - Name
  - Target folder
  - Passwords
- entity: download
  shows:
  - File name
  - Link
  - Hoster
  - Size
  - Online status
  - Error
  - Subfolder
  collects:
  - Link
  - Download password
entryPoints:
- haul-web: /linksammler
references:
- kind: code
  role: implementation
  target: ui/src/routes/Collector.tsx#CollectorPage
---

# Link grabber

Where links are pasted and where packages from every source wait to be checked, adjusted and started,
with a checkbox per file.
