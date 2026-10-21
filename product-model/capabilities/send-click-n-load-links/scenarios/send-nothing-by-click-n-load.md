---
kind: validation
routes:
  cnl: Click'n'Load
steps:
- text: The Link site posts a request without any link
  kind: actor
  actor: link-site
  entities: []
  contexts:
    cnl:
      place: click-n-load
- text: 'The Product answers failed: no links'
  kind: product
  actor: link-site
  entities: []
  contexts:
    cnl:
      place: click-n-load
---

# Send nothing by Click'n'Load

## Trigger

A site sends an empty or broken request.

## Outcome

Nothing is added.
