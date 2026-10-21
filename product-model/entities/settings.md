---
singleton: true
references:
- kind: code
  role: implementation
  target: crates/haul/src/db.rs#Settings
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#get_settings
- kind: doc
  role: intent
  target: docs/installation.md#settings-in-the-ui
---

# Settings

Haul's settings, kept once for the whole server.

## Information kept

- **Parallel downloads** — how many downloads run at once, 1 to 20, default 3
- **Connections per file** — 1 to 16, default 4; hosters may allow fewer
- **Bandwidth limit** — KiB/s over all downloads, 0 for no limit
- **Retries** — failed attempts allowed per download, 0 to 50, default 5
- **Extract finished packages automatically** — on by default
- **Delete archives after successful extraction** — off by default
- **Remove the downloads from the list after successful extraction** — off by default
- **Ask for the archive password when none fits** — on by default
- **Verify the checksum** — after the download, when the hoster publishes one; on by default
- **Archive passwords** — tried on every protected archive, the one that last opened an archive first
- **API token** — the token the browser extension and the desktop forwarder send; only whether one is set is shown
- **Running downloads folder** — where downloads in progress are kept
- **Finished files folder** — the done folder
- **Custom plugins folder** — where custom hoster plugins are loaded from
- **Extractors** — the archive extractors Haul found, best first
