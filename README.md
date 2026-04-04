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
| **Privacy Policy** | [privacy-policy.md](https://github.com/Chani1228/blovault-web/blob/main/privacy-policy.md) | Same path — use for Plaid “Privacy Policy URL” |
| **Terms of Service** | [terms-of-service.md](https://github.com/Chani1228/blovault-web/blob/main/terms-of-service.md) | Same path — use for “Terms URL” |

In the mobile app, the same texts are under **Settings → Data & Privacy → Privacy Policy / Terms of Service**.

---

## Plaid dashboard (quick paste)

| Field | Value |
|--------|--------|
| Privacy Policy URL | `https://github.com/Chani1228/blovault-web/blob/main/privacy-policy.md` |
| Terms of Service URL | `https://github.com/Chani1228/blovault-web/blob/main/terms-of-service.md` |
| Privacy / product contact | `privacy@blovault.com` (use an inbox you monitor) |
| Vulnerability disclosure (e.g. security questionnaire) | Use a dedicated address you check (e.g. `security@blovault.com`) |
