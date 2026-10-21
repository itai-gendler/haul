---
domain: accounts-and-plugins
references:
- kind: code
  role: implementation
  target: crates/haul/src/db.rs#Account
- kind: code
  role: implementation
  target: crates/haul/src/api.rs#run_account_check
- kind: code
  role: implementation
  target: crates/haul/src/engine/mod.rs#pick_account
- kind: doc
  role: intent
  target: docs/hosters.md#accounts
---

# Account

The user's account at one hoster, used for downloads and, where the plugin asks for it, for listing
folders.

## Information kept

- **Hoster** — the hoster plugin it belongs to
- **User** — user name or e-mail, empty where the hoster takes only a key or cookies
- **Password** — password, API key or browser cookies, as the plugin's form asks; stored encrypted and never shown again
- **Active** — whether Haul may use it
- **Premium** — Premium, No premium or Type unknown
- **Valid until** — the expiry date the hoster names
- **Traffic left** — the traffic the hoster reports
- **Last checked** — when the account was last checked
- **Error** — what the hoster said when the login failed
- **Hoster session** — the hoster login kept between calls and restarts

## States

### Unchecked

Saved but not checked yet.

### Checking

Haul is logging in to the hoster.

### Valid

The hoster accepted the login.

### Invalid

The hoster rejected the login; Haul does not use the account.

### Error

The check could not finish, for example because the hoster was unreachable.
