# BLO VAULT — Information Security Policy

**Version:** 1.0  
**Effective:** April 2026  
**Owner:** Chan Hong (BLO VAULT operator)  
**Classification:** Internal / Partner disclosure (Plaid)

---

## 1. Purpose and scope

This Information Security Policy (“Policy”) defines how **BLO VAULT** identifies, mitigates, and monitors information security risks for the **BLO VAULT** mobile application, its supporting backend services used as a **Plaid proxy**, and related operational processes.

**Scope includes:** iOS, Android, and macOS client builds distributed to end users; Supabase-backed Edge Functions and data stores used for Plaid token proxying; development, build, and release workflows; subprocessors listed in the public Privacy Policy.

**Out of scope:** Security programs of financial institutions, Plaid, Inc., Apple, Google, or other third parties (governed by their own policies).

This Policy is **operationalized** through documented procedures referenced below, tooling (CI/CD, monitoring), and periodic review.

---

## 2. Roles and responsibilities

| Role | Responsibility |
|------|----------------|
| **Operator / Developer (Chan Hong)** | Owns this Policy; implements controls in application and backend configuration; responds to incidents and vulnerability reports; approves subprocessors for production use. |
| **End users** | Protect device passcodes/biometrics; use in-app security features (e.g., session lock, Panic Delete) as appropriate. |

---

## 3. Information security program (continuous improvement)

BLO VAULT maintains an **information security program** that is **reviewed at least annually** and updated for changes in product architecture, applicable law (including U.S. state privacy laws and CCPA/CPRA), and partner requirements.

The program includes:

- **Risk identification:** Review of architecture (on-device financial data, encrypted token storage, network boundaries), threat scenarios (token exposure, unauthorized access, key compromise), and dependency/supply-chain risk.
- **Risk mitigation:** Technical and procedural controls in Sections 5–12.
- **Risk monitoring:** Automated testing in CI/CD, crash/diagnostic telemetry where enabled (Sentry), and manual review of critical changes.

---

## 4. Risk management methodology

1. **Identify** — Map data flows (Plaid → App → local encrypted store; App ↔ Supabase proxy; optional Sentry; subscriptions via Apple/Google/RevenueCat). Document assets and subprocessors.
2. **Mitigate** — Apply controls proportional to risk (encryption, access control, least privilege on backend, secure development practices).
3. **Monitor** — Run static analysis and tests in pipeline; track crashes and regressions; reassess after incidents or major releases.

---

## 5. Data classification and handling

| Category | Examples | Handling |
|----------|----------|----------|
| **Highly sensitive** | Plaid-linked financial transaction and balance data used in-app | Stored **only on the user device** in **AES-256** encrypted storage (SQLCipher). Not stored as raw ledger on BLO VAULT central servers. |
| **Sensitive** | Encrypted Plaid access tokens, minimal account metadata in Supabase | Encrypted at application layer before storage; access limited to authenticated user sessions and **Row Level Security (RLS)** on Supabase. |
| **Operational** | Build secrets, API keys (developer environment) | Stored outside public repositories; not committed to version control. |
| **Diagnostic** | Crash reports (if Sentry enabled) | Client configured to reduce identifiable user fields; governed by Sentry’s terms and project settings. |

**Biometric data:** Processed by the **OS** only; BLO VAULT does not store biometric templates.  
**SSN / government ID (OCR):** Not retained when excluded at capture/processing stages per product design.

---

## 6. Access control

- **Consumer access to the App:** **Face ID / Touch ID** or device PIN/passcode via platform APIs before access to financial data; **session timeout** (e.g., **5 minutes** of inactivity) requiring re-authentication.
- **Backend / Supabase:** Access via **short-lived JWTs** tied to user sessions; **RLS** restricts data to the owning user. Developer access to Supabase dashboard follows vendor best practices (e.g., **SSO** where configured).
- **Principle of least privilege:** No standing employee access to end-user financial ledger content on servers (by architecture: raw transaction history is not centralized on BLO VAULT servers).

---

## 7. Cryptography and transmission security

- **Data at rest (device):** **AES-256** (SQLCipher); key material protected via **iOS Keychain / Android Keystore** (or equivalent secure storage).
- **Data in transit:** **HTTPS (TLS)** for all application traffic to BLO VAULT-controlled and configured services. For **critical API endpoints** (including Supabase and other client-configured domains), **certificate public-key pinning** is used **where supported by the platform**, consistent with partner security disclosures.
- **Tokens:** Plaid access tokens are **encrypted** before persistence in Supabase.

---

## 8. Secure development and change management

- **Secure SDLC practices** aligned with **OWASP Mobile Top 10** awareness; security-minded design for authentication, storage, and Plaid integration.
- **Automated checks:** **GitHub Actions** CI runs **static analysis** (`flutter analyze`), **automated tests**, and **dependency vulnerability scanning** on security-relevant paths.
- **Code review:** Security-sensitive changes reviewed before merge where practicable for solo-operator workflow.
- **Planned hardening (roadmap):** Additional controls (e.g., jailbreak/root detection, tamper detection, expanded memory hygiene) are tracked against the main product roadmap and rolled in as implemented.

---

## 9. Vulnerability and patch management

- **Dependency and supply chain:** Monitor advisories; upgrade packages per severity-based targets (e.g., **Critical ~24h**, **High ~72h**, **Medium ~7 days**) where feasible for a small team.
- **Disclosure intake:** Security issues may be reported to **info@blovault.com** (temporary); acknowledgment targeted within **48 hours**; status updates within **7 days** when practical; remediation timelines aligned with severity.
- **Formal security@ address** and published VDP page are planned when `@blovault.com` mail is available (see repository **FUTURE.md**).

---

## 10. Incident response

Documented response paths include:

| Scenario | Initial steps |
|----------|----------------|
| **Suspected Plaid token exposure** | Suspend or limit affected Edge Function paths if needed; invoke **Plaid `/item/remove`** for impacted items; notify affected users as required; document for GLBA-aligned financial privacy obligations where applicable. |
| **Encryption key compromise** | Guide users through **Panic Delete** / re-enrollment; rotate server-side secrets and keys per runbooks. |
| **Unauthorized access / abuse** | Suspend affected services as needed; preserve logs per retention; root-cause analysis; user notification per legal requirements (e.g., breach timelines under applicable law). |

Incidents are logged; post-incident review updates controls and this Policy as needed.

---

## 11. Vendor and third-party management

Subprocessors (e.g., **Plaid**, **Supabase**, **RevenueCat**, **Apple**, **Google**, **Sentry**) are selected for fit with BLO VAULT’s architecture. Contracts or standard terms are accepted per vendor. Consumer-facing disclosures appear in the **Privacy Policy** (`privacy-policy.md`). Changes to material subprocessors trigger Privacy Policy updates.

---

## 12. Data retention and secure disposal

Aligned with the **Data Retention and Disposal** practices supplied with the Plaid production package:

| Data type | Retention (summary) | Disposal method |
|-----------|---------------------|-----------------|
| **Financial transaction data (on-device)** | Active subscription period **+ 44 days** (grace / wind-down) | **AES-256** encrypted local wipe; user **Panic Delete** |
| **Plaid access tokens** | Revoked within a **defined period after subscription termination** | Supabase secure deletion + **Plaid `/item/remove`** |
| **W-2 / tax-related OCR extracts** (if feature enabled) | **7 years** (IRS-aligned), **local encrypted storage only** | Secure local deletion per legal retention completion |
| **Account metadata (backend)** | **44 days** post-subscription (where applicable) | Local DB wipe + Supabase deletion workflows |
| **Biometric data** | Not stored by BLO VAULT | N/A (OS-only) |
| **SSN fields** | Not stored — excluded at OCR stage | Volatile handling per design |

**Disposal sequence (subscription end — target procedure):**  
**T+0:** `/item/remove` for linked items to stop third-party billing where applicable.  
**T+14 days:** Data may remain encrypted with access locked during grace.  
**T+44 days:** Target completion of permanent deletion from local device and Supabase for covered categories (subject to tax-record exception above).

*Operational automation of every timing target is implemented incrementally; until automated, **manual and user-initiated deletion** (including Panic Delete) satisfies immediate user requests.*

---

## 13. Monitoring and logging

- **Application stability:** Optional **Sentry** for crashes/performance; configuration minimizes PII in events.
- **Backend:** Supabase and Edge Function logs used for abuse detection, rate limiting (e.g., requests per user), and incident investigation, within retention limits of the platform.

---

## 14. Policy review and distribution

- **Review frequency:** At least **annually**, and after material incidents or architecture changes.
- **Distribution:** Published in the **blovault-web** repository for partner and auditor reference; summaries reflected in consumer Privacy Policy where appropriate.
- **Versioning:** Version and effective date updated at top of document when revised.

---

## 15. Contact

**Information security / privacy (temporary):** info@blovault.com  

---

*This document supports Plaid and similar partner security questionnaires. It does not constitute legal advice. Align runtime controls and automation with stated procedures before representing full operational maturity.*
