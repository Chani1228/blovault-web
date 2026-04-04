# BLO VAULT — Future setup (checklist)

Items to close out when hardening **domain, legal, and security** for the public site (`blovault-web`), the app, and day-to-day operations. (Temporary contact is a personal Gmail today — see **Contact / branding** below.)

## Contact / branding

- [ ] **`@blovault.com` email** — Create `privacy@`, `support@`, `security@` (or split roles), then replace everywhere: app, policies, Plaid, stores.
- [ ] **Single canonical support address** — Same address in App Store, Play, Plaid, and vulnerability disclosure copy.
- [ ] **Formal VDP** — `security@` or a dedicated security page; replace the temporary Gmail paragraph in this repo’s README.
- [ ] (Optional) **GitHub Pages custom domain** — e.g. `legal.blovault.com` → Pages for this repository.

## Legal / policy

- [ ] **Attorney review** — Final pass on Privacy Policy and Terms of Service (and any follow-up edits after launch).
- [ ] **Data retention & deletion** — If you adopt fixed retention (e.g. after subscription ends), align policy copy, app behavior, and backend jobs.
- [ ] **CCPA / U.S. state laws** — Keep `legal/` docs and the in-app CCPA screen aligned with how you actually intake requests (email workflow, SLAs).
- [ ] **Store label parity** — Before each release, reconcile **App Store Privacy Nutrition Labels** and **Google Play Data safety** with `privacy-policy.md` §§3–6 and **real** collection/processing.

## Security / engineering (sync with app roadmap)

- [ ] **TLS certificate public-key pinning** — Ship pinning in the client for configured hosts (e.g. Supabase) so runtime behavior matches Privacy Policy §10 and Plaid security answers.
- [ ] **Jailbreak / root detection** — If added, update policy and store listings.
- [ ] **Auth failures / Panic Delete** — If you define thresholds (e.g. N failed attempts), match implementation and docs.
- [ ] **Sentry & Supabase** — Document production projects, RLS, and key-rotation runbooks.

## Plaid / partners

- [ ] **Production application PDF** — Re-check URLs, emails, and screenshots after the items above.
- [ ] **Data retention attachment** — Upload the final internal policy once it is fixed.

## This repository (`blovault-web`)

- [ ] **Enable GitHub Pages** (if not already) — Branch `main`, folder `/ (root)`. Surfaces `index.html` and [`privacy-policy.html`](privacy-policy.html) / [`view.html`](view.html) (Markdown rendered for easy reading).
- [ ] **README “Current product configuration”** — Periodically sync with the main **blo-vault** app repo.

---

*Last updated: 2026-04-04*
