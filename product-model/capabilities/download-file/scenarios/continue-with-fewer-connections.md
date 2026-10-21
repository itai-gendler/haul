---
kind: edge
routes:
  web: Haul web
steps:
- text: The hoster refuses an extra connection while another part of the file is loading
  kind: condition
  unattended: true
  entities:
  - entity: download
    effect: reads
    facts:
    - Progress
  contexts:
    web:
      place: haul-web::signed-in::downloads
- text: The Product lets the refused part wait and ask again, so the file loads with fewer connections
  kind: product
  entities:
  - entity: download
    effect: changes
    facts:
    - Progress
  contexts:
    web:
      place: haul-web::signed-in::downloads
---

# Continue with fewer connections

## Trigger

A free download allows fewer connections than Connections per file.

## Outcome

The download keeps going instead of failing, and its direct address is not lost.
