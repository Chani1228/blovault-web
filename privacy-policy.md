# BLO VAULT Privacy Policy

**Last Updated:** April 11, 2026

BLO VAULT ("we," "us," "our") is committed to protecting your privacy. This Privacy Policy explains how we collect, use, share, and safeguard your information when you use our mobile application (the "App"). BLO VAULT is operated by an individual developer (Chan Hong). We designed the App so that sensitive financial details stay on your device whenever possible.

**In-app:** Settings → Data & Privacy → Privacy Policy.  
**Public copy (GitHub — always works):** https://github.com/Chani1228/blovault-web/blob/main/privacy-policy.md  
**Easy read (GitHub Pages — enable Pages first):** https://chani1228.github.io/blovault-web/privacy-policy.html

---

## At a glance

- **Plaid:** You connect banks through Plaid; we act only as needed to access and refresh data you authorize. Transaction and balance data used in the App are stored primarily **on your device** in an encrypted database.
- **No central copy of your raw transaction history:** We do not store, use, or possess your full raw financial ledger on our servers.
- **Supabase:** We use it as a secure proxy; **encrypted Plaid access tokens** and limited metadata are stored there. If you send **in-app feedback** (text and optional screenshot), that content is also stored on Supabase for review and product improvement.
- **AI:** Analysis runs **on-device** (Gemma / Cactus SDK). We do not send your financial ledger to cloud LLM providers for inference in the standard App configuration.
- **Subscriptions:** Apple, Google, and/or RevenueCat process payments under their policies.
- **Diagnostics:** If enabled, **Sentry** may receive crash/performance data with client-side scrubbing of identifiable user fields.
- **You can wipe local data** with **Panic Delete** in Settings and disconnect Plaid items as described below.

---

## 1. Scope

This policy applies to the BLO VAULT App on iOS, Android, and macOS where distributed. It does not apply to third-party sites or flows (for example, Plaid Link, your bank, or app stores) — those are governed by their own terms and policies.

## 2. Data collection and use (Plaid and financial data)

BLO VAULT uses **Plaid Inc.** ("Plaid") to connect your financial accounts. By linking an account, you authorize Plaid and us to access and transmit personal and financial information from the relevant financial institution as described in Plaid’s interface and disclosures.

- **On-device storage:** Retrieved financial data used in the App is stored **exclusively on your mobile device** in an **AES-256** encrypted local database (SQLCipher).
- **No server-side storage of raw ledger:** We do **not** store your full raw transaction history on our central servers. Our backend holds **encrypted Plaid access tokens** and limited metadata needed to operate linking and token refresh.

Categories Plaid may share with the App can include institution and account identifiers, account types, balances, transaction details, **investment holdings**, and **other categories your institution exposes through Plaid** — as shown during linking and under Plaid’s consumer disclosures.

### 2.1 Optional in-app feedback

If you use the feedback feature (for example, **Settings → Send feedback**), you may submit a text message and optionally attach a screenshot. We store that content on our backend (**Supabase**, including file storage for images) to triage bugs, improve the App, and respond when needed. It may be associated with your **pseudonymous Supabase user identifier**. Do not include passwords, full account numbers, card numbers, or other secrets in feedback text. Screenshots may unintentionally show sensitive information — crop or avoid sensitive screens if you prefer not to share them.

## 3. Local AI processing

All financial analysis and AI inference for the on-device features are performed on your device using the **Gemma (Cactus SDK)** engine. Model files are downloaded to your device from **third-party distribution infrastructure** used by the SDK; those downloads are for model weights and assets, not for uploading your transaction content to a remote inference service in the standard configuration we describe in product materials.

## 4. Third-party service providers

We **do not sell** your personal information. We use service providers (subprocessors) as needed:

| Provider | Role |
|----------|------|
| **Plaid Technologies, Inc.** | Linking and financial data access. See [Plaid Legal](https://plaid.com/legal/). |
| **Supabase** | Authentication; Edge Functions that proxy Plaid API calls; storage of encrypted Plaid tokens; storage of optional user feedback and attachments (Section 2.1). |
| **RevenueCat** | Subscription entitlements and paywall infrastructure. |
| **Apple / Google** | In-app purchases, platform services, and (if you use optional speech-to-text) operating-system speech processing under their respective privacy policies. |
| **Sentry** | Optional crash and performance diagnostics if a DSN is configured. [Sentry Privacy](https://sentry.io/privacy/) |
| **Google ML Kit** (or similar) | On-device text recognition when you use receipt scanning, where applicable. |
| **Reference data hosts** | Some features may request non-identifying reference or market data over HTTPS (for example, public ticker or index information) solely to power in-App calculations or illustrations. |

Each provider processes data under its own terms and privacy notices.

## 5. Authentication and session

- **Device unlock:** Face ID, Touch ID, or device PIN/passcode via the operating system. We do **not** receive or store biometric templates.
- **Backend:** Supabase issues a session (JWT) so the App can call our proxy. This may include a pseudonymous user identifier managed by Supabase.

## 6. Subscription and purchase data

Purchases are processed by **Apple**, **Google**, and/or **RevenueCat**. They may collect billing and device identifiers under their policies. We receive **entitlement information** (for example, Pro vs Free) to enforce plan limits such as the number of linked accounts.

## 7. How we use information

We use information to operate and improve the App; link and refresh accounts; enforce tiers; **process optional feedback you submit**; fix crashes (if Sentry is on); comply with law; and respond when you contact us.

## 8. Legal bases (where applicable)

Where the **GDPR**, **UK GDPR**, or similar laws apply, we rely on contract performance, consent where required (including Plaid linking), and legitimate interests in security and improvement, balanced against your rights.

## 9. Data retention and deletion

- **On-device** data remains until you delete it (Panic Delete or uninstall).
- **Encrypted tokens** and related metadata on Supabase remain until you remove linked items, revoke access through Plaid or the App where available, or we delete them in connection with support or closure processes.
- **Feedback** records and attachments on Supabase are retained for as long as needed to operate support and improve the App unless we delete them earlier or you ask us to delete them where applicable law requires.
- **Sentry** data is retained per Sentry project settings.

We **do not** state an automated “subscription end + fixed-day” server purge unless and until that process is implemented and documented in this policy.

## 10. Data security

We use industry-appropriate measures, including: **AES-256** encryption at rest on device; OS secure storage (e.g., iOS Keychain / Android Keystore) for key material; and **HTTPS (TLS)** for data in transit between the App and our backend and other configured hosts.

**Certificate public-key pinning is not enabled in all builds:** where the shipping client includes configured pin hashes and an explicit opt-in build flag, additional certificate checks may apply; otherwise the App relies on the platform’s **standard TLS chain validation** (including OS trust store updates). We do **not** claim universal pinning in every distributed build.

## 11. Your rights (CCPA, U.S. state laws, and others)

Depending on where you live, you may have the right to access, delete, or correct personal information we hold; to opt out of certain processing; or to appeal.

### 11.1 California (CCPA/CPRA)

You may have the rights to know, delete, and correct. We **do not sell** personal information as defined by the CCPA. Use in-app controls (Data & Privacy, Panic Delete) and email us below. We will not discriminate for exercising these rights.

### 11.2 Other U.S. states

Residents of states with comprehensive privacy laws may have similar rights — contact us with your request.

### 11.3 EEA, UK, Switzerland

You may have GDPR-related rights, including lodging a complaint with a supervisory authority.

Federal financial privacy rules such as **GLBA** primarily govern **financial institutions**; if you have questions about how they apply to your bank or broker, consult that institution’s privacy notice.

## 12. Children’s privacy

BLO VAULT does **not** knowingly collect personal information from anyone under **13** (or the minimum age required in your region). If you believe we have, contact us and we will take appropriate steps.

## 13. International users

We are based in the **United States**. Your information may be processed in the U.S. and in locations where subprocessors operate. We use appropriate safeguards where required by law.

## 14. Beta and test programs

If you install a **pre-release or beta** build (for example through **Apple TestFlight** or similar), the platform provider may collect additional diagnostics, crash data, or usage metadata under its beta program terms, in addition to the practices described in this Policy.

## 15. Changes to this policy

We may update this policy. We will post the new version in the App and on our public page and change the **Last Updated** date. Continued use where permitted by law constitutes acceptance of the updated policy.

## 16. Contact

**info@blovault.com**

For privacy requests, include enough detail for us to verify and process your request. We will respond within timeframes required by applicable law.
