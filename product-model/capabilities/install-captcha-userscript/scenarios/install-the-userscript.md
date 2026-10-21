---
kind: primary
routes:
  web: Haul web
steps:
- text: The User follows the userscript's install link
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
- text: The Product serves the userscript for the browser's userscript manager to install
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: haul-web::signed-in::settings
---

# Install the userscript

## Trigger

Hosters the user uses show captchas that work only on their own pages.

## Outcome

The browser runs the userscript on hoster pages Haul opens with a captcha task.

## Edge cases

- Some browsers run it only after user scripts are allowed for the userscript manager; until then Solve opens the full hoster page.
