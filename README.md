# blovault-web

Public static site for **BLO VAULT** — legal pages and partner disclosure links (Plaid, app stores, etc.).

**Repository:** [github.com/Chani1228/blovault-web](https://github.com/Chani1228/blovault-web)

Optional: enable **GitHub Pages** (Settings → Pages → Deploy from `main`) to serve [`index.html`](index.html) at  
`https://chani1228.github.io/blovault-web/` — legal URLs below work either way.

---

## Current product configuration (April 2026)

Mirrors the shipping **blo-vault** app repo at a high level (not legal advice).

| Area | Implementation |
|------|----------------|
| **Client** | Flutter (iOS, Android, macOS) |
| **Local data** | SQLite via **SQLCipher** (AES-256); keys in **iOS Keychain / Android Keystore** (`flutter_secure_storage`) |
| **Auth to app** | **Face ID / Touch ID** and device PIN/passcode via `local_auth`; **5-minute** idle session auto-lock |
| **Bank linking** | **Plaid**; **Supabase** Edge Functions as **Plaid proxy only** |
| **Server-stored secrets** | **Encrypted** Plaid access tokens only — not raw transaction payloads |
| **AI** | **On-device** — Gemma 3 via **Cactus SDK**; financial content not sent to model hosts |
| **History window** | Up to **24 months** of transactions analyzed on-device (app constant) |
| **Monetization** | **RevenueCat**; free tier **3** linked Plaid accounts |
| **User wipe** | **Panic Delete** (Settings): clears local DB, secure storage, and local cache boxes |
| **Crash reporting** | **Sentry** (configurable via env); PII scrubbing in client |

**Not claimed here as shipped:** certificate public-key pinning, jailbreak/root gating, automated subscription-based server purge schedules — see main app roadmap in the private **blo-vault** repo.

---

## Legal documents

| Document | GitHub (rendered) | Raw |
|----------|-------------------|-----|
| **Privacy Policy** | [privacy-policy.md](https://github.com/Chani1228/blovault-web/blob/main/privacy-policy.md) | Expanded for **Plaid / App Store / Play** review: collection categories, subprocessors, retention, rights, children, international |
| **Terms of Service** | [terms-of-service.md](https://github.com/Chani1228/blovault-web/blob/main/terms-of-service.md) | Subscriptions/refunds (platform rules), service changes, liability cap, Delaware + informal dispute step |

In the mobile app, the same substance is under **Settings → Data & Privacy → Privacy Policy** (bundled `assets/legal/privacy_policy.txt`).

**Store consoles:** align **Apple Privacy Nutrition Labels** and **Google Play Data safety** with Privacy Policy §3 — mismatches are a common rejection reason, not “policy length” alone.

**Planned upgrades** (domain email, legal finalization, security hardening): see **[FUTURE.md](FUTURE.md)**.

---

## Vulnerability disclosure (temporary)

Security researchers may report issues to **chan.hong1228@gmail.com**. Include steps to reproduce, affected component, and severity if known. We aim to acknowledge within **48 hours** and provide status updates when practical. **Replace with `security@blovault.com` (or a formal VDP page) when domain mail is live** — see [FUTURE.md](FUTURE.md).

---

## Plaid dashboard (quick paste)

| Field | Value |
|--------|--------|
| Privacy Policy URL | `https://github.com/Chani1228/blovault-web/blob/main/privacy-policy.md` |
| Terms of Service URL | `https://github.com/Chani1228/blovault-web/blob/main/terms-of-service.md` |
| Support / privacy / security (temporary) | `chan.hong1228@gmail.com` — single inbox until `@blovault.com` addresses exist |
