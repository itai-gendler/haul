---
references:
- kind: code
  role: implementation
  target: crates/haul/src/db.rs#Download
- kind: code
  role: implementation
  target: crates/haul/src/db.rs#status
- kind: code
  role: implementation
  target: crates/haul/src/engine/worker.rs#execute
- kind: code
  role: implementation
  target: ui/src/components/status.ts#describe
- kind: doc
  role: intent
  target: docs/architecture.md#the-life-of-a-download
---

# Download

One link and the file behind it, from the moment it is added until the file is in the done folder.

## Information kept

- **Link** — the address as it was added
- **File name** — a placeholder from the link until the hoster or the server names the file
- **Size** — when the hoster or the server tells it
- **Hoster** — the hoster plugin that handles the link, or none for a direct link
- **Online status** — Online, Unchecked or File offline
- **Progress** — bytes already loaded, kept across pauses and restarts
- **Error** — why the last attempt failed or why it waits
- **Attempts** — failed attempts counted against the Retries setting
- **Next try** — when a waiting download may start again
- **Checksum** — the kind of checksum the hoster published, if any
- **Checksum result** — verified or checksum wrong
- **Download password** — the password of a protected file or folder; never shown again
- **Subfolder** — the folder below the package folder a crawled file belongs in
- **Finished at** — when the file was finished

## States

### In the link grabber

Added and checked online, waiting to be started.

### Reading folder

A folder link whose files the hoster plugin is listing; it is replaced by them.

### Waiting

In the queue, possibly until its next try.

### Connecting

The hoster plugin is getting the file's direct address; a captcha or password question may be open.

### Downloading

Bytes are arriving, followed by the checksum check where there is one.

### Paused

Stopped by the user; the loaded bytes are kept.

### Finished

The file is in its folder.

### Failed

Offline, refused, out of retries or cancelled; it needs the user.
