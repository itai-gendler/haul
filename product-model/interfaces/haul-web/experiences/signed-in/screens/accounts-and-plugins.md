---
entities:
- entity: account
  shows:
  - Hoster
  - User
  - Active
  - Premium
  - Valid until
  - Traffic left
  - Last checked
  - Error
  collects:
  - Hoster
  - User
  - Password
- entity: hoster-plugin
  shows:
  - Name
  - Version
  - Domains
  - Link patterns
  - Origin
  - File
  - Needs an account
  - Account form
  - Replaces
entryPoints:
- haul-web: /accounts
references:
- kind: code
  role: implementation
  target: ui/src/routes/Accounts.tsx#AccountsPage
---

# Accounts & plugins

The hoster accounts with their state, type, expiry and traffic, the form to add one, and the loaded
hoster plugins with their version, origin and link patterns.
