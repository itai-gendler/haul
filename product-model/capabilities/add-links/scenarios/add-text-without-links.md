---
kind: validation
routes:
  web: Haul web
steps:
- text: The User pastes text that contains no http(s) link and chooses Add
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
- text: The Product refuses and says no valid link was found
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::link-grabber
---

# Add text without links

## Trigger

The pasted text has no usable link.

## Outcome

Nothing is added.
