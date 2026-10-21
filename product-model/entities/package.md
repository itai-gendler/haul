---
relations:
- entity: download
  verb: holds
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: crates/haul/src/db.rs#Package
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#add_links
- kind: code
  role: implementation
  target: crates/haul/src/engine/extract.rs#extract_package
- kind: doc
  role: context
  target: docs/architecture.md#the-life-of-a-download
---

# Package

A group of links added together. A package owns the target folder its files land in and the passwords
tried on its archives, and it is extracted as a whole once all its downloads are finished.

## Information kept

- **Name** — given by the user, or derived from the file names or the crawled folder
- **Target folder** — the folder inside the done folder its files go to; the package name by default
- **Source** — manual, browser extension or Click'n'Load
- **Source page** — the page the links came from, when known
- **Passwords** — archive passwords of this package, one per line; the first may also serve as download password
- **Extraction error** — why the last extraction failed, naming each extractor tried or the missing part

## States

### In the link grabber

Collected and waiting for the user to check and start it; nothing downloads.

### In the downloads

Started; its links are in the queue or finished.

### Extracting

Its archives are being extracted, with a percentage.

### Extracted

Every archive set of the package opened.

### Extraction failed

At least one archive could not be extracted; the error says why.
