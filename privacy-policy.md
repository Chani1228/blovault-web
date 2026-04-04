# BLO VAULT Privacy Policy

**Last updated:** 2026-04-04

**In-app:** **Settings** → **Data & Privacy** → **Privacy Policy**.

**Public copy (this page):**  
https://github.com/Chani1228/blovault-web/blob/main/privacy-policy.md  
(Use for partner disclosures, e.g. Plaid.)

---

This Privacy Policy describes how BLO VAULT ("we," "us," "our") collects, uses, shares, and protects information when you use our mobile application (the "App"). BLO VAULT is operated by an individual developer (Chan Hong). We designed the App so that sensitive financial details stay on your device whenever possible.

This policy is a draft and does not replace legal advice. We recommend independent review before relying on it for regulatory filings.

## 1. Scope

This policy applies to the BLO VAULT App on iOS, Android, and macOS where distributed. It does not apply to third-party websites or services that we link to (for example, Plaid’s or your bank’s interfaces).

## 2. Summary (quick read)

- You connect accounts through **Plaid**. Transaction and balance data used in the App are stored primarily **on your device** in an encrypted database.
- Our backend (**Supabase**) is used as a **Plaid proxy**. We store **encrypted Plaid access tokens** and related non-financial metadata needed to operate linking — **not** your full transaction history on our servers.
- **AI features run on your device** (Cactus SDK / on-device models). We do **not** send your transaction content to remote AI inference servers for those features.
- **Subscriptions** are processed by **Apple**, **Google**, and/or **RevenueCat** under their terms.
- If enabled, **crash diagnostics** may be sent to **Sentry** with identifiers scrubbed in our client configuration.
- You can wipe local data using **Panic Delete** in Settings.

## 3. Information we collect

### 3.1 Financial and account information (Plaid)

When you choose to link a financial institution, Plaid collects and shares data with the App according to Plaid’s flow and your consent. Categories may include: institution name, account identifiers, account types, balances, and transaction details. That data is processed in the App and stored on your device in an **AES-256 encrypted local database (SQLCipher)**. We do **not** upload your raw transaction history to our own servers for storage.

### 3.2 Authentication and app session

- **Device unlock:** We use the operating system’s biometric APIs (Face ID, Touch ID, or device PIN/passcode) via the device. We do **not** receive or store biometric templates.
- **Backend session:** We use **Supabase** with an anonymous or authenticated session (JWT) so the App can call our Plaid proxy. This may include a pseudonymous user ID and session tokens managed by Supabase.

### 3.3 Subscription and purchase data

Purchases and entitlements may be processed by **Apple App Store**, **Google Play**, and **RevenueCat**. They may collect payment-related and device identifiers under their policies. We receive **entitlement status** (for example, whether you have an active subscription) to enforce plan limits.

### 3.4 Diagnostics and performance (optional)

If a valid Sentry DSN is configured, the App may send crash reports and performance data to **Sentry**. Our client is configured to avoid attaching identifiable user profile fields to events (for example, user context is set to a non-identifying label). [Sentry’s privacy notice](https://sentry.io/privacy/) governs their processing.

### 3.5 Receipt scanning / OCR (optional)

If you use receipt scanning, images and extracted text are processed to operate the feature. Processing is designed to occur **on-device** using on-device ML where applicable. Do not scan documents you are not permitted to process.

### 3.6 On-device AI models

To run AI features, model files may be **downloaded** to your device. Downloads are for model weights and related assets, not for uploading your financial ledger to a model host for inference in the standard configuration described in our product documentation.

### 3.7 Technical and usage data

Like most apps, we may process limited technical data through subprocessors (for example, device/OS version in diagnostics, or metadata required for API calls). We do **not** sell your personal information.

## 4. How we use information

We use information to: provide and maintain the App; link and refresh accounts via Plaid; enforce subscription tiers and free-tier limits; improve stability and fix crashes (if Sentry is enabled); comply with law; and communicate with you when you contact us.

## 5. Legal bases (where applicable)

Where laws such as the GDPR or UK GDPR apply, we rely on: (a) performance of a contract (providing the App you requested); (b) consent where required (for example, linking accounts through Plaid); and (c) legitimate interests in securing and improving the App, balanced against your rights.

## 6. Sharing and subprocessors

We do **not** sell your personal information. We share data with service providers as needed to run the App, including:

| Provider | Role |
|----------|------|
| **Plaid Technologies, Inc.** | Account linking and financial data access. See [Plaid Consumer Privacy Policy](https://plaid.com/legal/#consumers). |
| **Supabase** | Authentication and backend functions that proxy Plaid API calls; storage of encrypted Plaid tokens as described above. |
| **RevenueCat** | Subscription status and paywall infrastructure. |
| **Apple / Google** | In-app purchases and platform services. |
| **Sentry** | Optional crash reporting (if configured). |
| **Google ML Kit** (or similar) | On-device text recognition where used for receipt features. |

Third parties process data under their own terms.

## 7. Retention

- **On-device** financial data remains on your device until you delete it (for example, via Panic Delete or uninstalling the App).
- **Encrypted Plaid tokens** and minimal account metadata on Supabase persist until you disconnect items, revoke access, or we delete them as part of account closure processes.
- **Sentry** data is retained according to Sentry’s settings and our project configuration.

Specific retention schedules may evolve; material changes will be reflected in this policy.

## 8. Security

We use industry-appropriate measures for a consumer financial app, including: encrypted local storage (SQLCipher); OS secure storage for keys; TLS for network communications; and access controls on backend resources. No method of transmission or storage is 100% secure.

## 9. Your rights and choices

Depending on where you live, you may have rights to access, correct, delete, or export personal data; to opt out of certain processing; or to appeal decisions.

### 9.1 California (CCPA/CPRA)

California residents may have rights to know, delete, and correct personal information, and to opt out of sale/sharing. We do **not** sell personal information as defined by the CCPA. You may use in-app controls (for example, Data & Privacy and Panic Delete) and contact us using the email below. We will not discriminate for exercising these rights.

### 9.2 Other U.S. states

Residents of other states with privacy laws may have similar rights. Contact us with your request.

### 9.3 European Economic Area, UK, Switzerland

You may have GDPR-related rights, including to lodge a complaint with a supervisory authority.

## 10. Children

The App is not directed to children under 13 (or the minimum age required in your region). We do not knowingly collect personal information from children. If you believe we have, contact us and we will take appropriate steps.

## 11. International users

We are based in the United States. If you use the App from other countries, your information may be processed in the U.S. and other locations where our subprocessors operate. We rely on appropriate safeguards where required by law.

## 12. Changes to this policy

We may update this policy from time to time. We will post the updated version in the App and on our public policy page and update the "Last updated" date. Continued use after changes means you accept the updated policy, to the extent permitted by law.

## 13. Contact (temporary — no @blovault.com yet)

**chan.hong1228@gmail.com**

For privacy requests, include enough detail for us to verify and process your request. We will respond within the timeframes required by applicable law.

---

**DRAFT — Attorney review recommended before production launch and before regulatory reliance.**
