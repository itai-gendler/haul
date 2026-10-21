---
availability:
- place: haul-web::signed-out
- place: haul-web::signed-in
references:
- kind: code
  role: implementation
  target: ui/src/i18n.ts#setLang
- kind: code
  role: implementation
  target: ui/src/components/Layout.tsx#LanguageSwitch
- kind: code
  role: implementation
  target: crates/haul/src/i18n.rs
---

# Change language

The user switches the interface between German and English for this browser, on the login page, in the sidebar or under Settings → Language. Every text follows, including messages from the server and the hoster plugins.
