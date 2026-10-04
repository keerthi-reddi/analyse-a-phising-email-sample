# analyse-a-phising-email-sample
# Cybersecurity Task: Phishing Email Technical Analysis & Header Audit

## Executive Summary
- **Target Recipient:** `john.doe@mybusiness.com`
- **Impersonated Sender:** Remitly Financial Services
- **Attack Vector:** Domain Spoofing, Authentication Failure (SPF/DMARC), Credential Harvesting

---

## Technical Examination & Findings (Steps 1–8)

### 1. Sample Phishing Email
Analyzed a credential-harvesting phishing lure targeting corporate credentials under the pretense of an urgent transaction reversal.

### 2. Sender Email Address Analysis
* **Display Name:** `Remitly Team`
* **Header Sender (`From:`):** `remitly.team@alerting-services.com`
* **Spoofing Indicator:** The display name claims representation of `remitly.com`, but the envelope sending domain is `alerting-services.com`.

### 3. Email Header Discrepancies
* **Raw Header Extracted:**
  ```text
  Received: from mail-gateway.alerting-services.com (198.51.100.45)
      by mx.google.com with ESMTPS id p188si20261004h32.12.2026.10.04.21.15.30
      for <john.doe@mybusiness.com>; Sun, 04 Oct 2026 21:15:30 +0530
  Return-Path: <bounce-285k-remitly@alerting-services.com>
  Authentication-Results: mx.google.com;
      spf=fail (google.com: domain of alerting-services.com does not designate 198.51.100.45 as permitted sender) client-ip=198.51.100.45;
      dkim=neutral (message not signed);
      dmarc=fail (p=REJECT dis=NONE) header.from=remitly.com
  From: "Remitly Team" <remitly.team@alerting-services.com>
  To: "John Doe" <john.doe@mybusiness.com>
  Subject: Your Payment Status - Transfer #285000-PENDING
  SPF Failure: spf=fail — Server IP 198.51.100.45 is not an authorized sender for the claimed domain.

DKIM Neutral/Missing: dkim=neutral — The email lacks a valid cryptographic DKIM signature proving integrity.

DMARC Failure: dmarc=fail (p=REJECT) — Misalignment between the header From: domain (remitly.com) and the sending server domain (alerting-services.com).

4. Suspicious Links and Attachments
Attachments: No direct file attachments present.

Identified Link: Primary call-to-action button directing users to an external authentication portal.

5. Urgent or Threatening Language
Urgency Trigger: Asserts that an unauthorized transfer of $285,000.00 USD is pending.

Threat Window: Claims the funds will become irreversible within 24 hours unless verified immediately.

6. Mismatched URLs
Visible Link Text: https://www.remitly.com/transaction/reversal

True Target URL (href): https://login.alerting-services.com/auth/login?user=john.doe@mybusiness.com

Deception Technique: Mismatched anchor text used to redirect victims to a third-party login harvester.

7. Spelling, Grammar, and Formatting Anomalies
Uses generic corporate greetings ("Dear Customer / Contoso Corp") rather than authentic personal account attributes, alongside non-standard header casing.

8. Summary of Phishing Traits Found
Domain Spoofing: Display name misrepresents the actual sending domain.

Authentication Failures: Complete failure of SPF and DMARC checks.

Hyperlink Deception: Discrepancy between visible anchor text and actual destination URL.

Coercive Financial Lure: High monetary urgency designed to induce panic and hasty compliance.
