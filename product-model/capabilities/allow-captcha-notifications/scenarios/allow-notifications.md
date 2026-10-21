---
kind: primary
routes:
  web: Haul web
steps:
- text: The User chooses Allow notifications and the browser asks for permission
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The User allows notifications for Haul
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The Product shows that notifications are on, and from now on each new question in the banner shows a browser
    notification while the tab is in the background
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Allow notifications

## Trigger

The user often has Haul in a background tab.

## Outcome

New captchas and password questions announce themselves.

## Edge cases

- When the browser blocks notifications, the page says so and offers nothing to click.
