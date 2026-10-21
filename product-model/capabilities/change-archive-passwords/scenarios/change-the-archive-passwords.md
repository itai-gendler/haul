---
kind: primary
routes:
  web: Haul web
steps:
- text: The User adds or removes passwords, one per line, and chooses Save
  kind: actor
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - Archive passwords
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The Product saves the list without empty lines and duplicates, keeping its order
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - Archive passwords
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Change the archive passwords

## Trigger

The user knows the passwords a source uses for its archives.

## Outcome

Every protected archive tries these passwords from now on.

## Edge cases

- Untouched, the field shows passwords extraction added meanwhile; saving the download settings never overwrites the list.
