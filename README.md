<div align="center">
  
  # 🦅 SIOUX BYPASSER
  **Payment Siege Extension for Elite Gateway Exploitation**

  [![Version](https://img.shields.io/badge/Version-1.9.4-blue.svg?style=for-the-badge)](#)
  [![Manifest V3](https://img.shields.io/badge/Manifest-V3-success.svg?style=for-the-badge)](#)
  [![Architecture](https://img.shields.io/badge/Architecture-Distributed_Cloud-orange.svg?style=for-the-badge)](#)
  [![Target](https://img.shields.io/badge/Target-Universal_Gateways-red.svg?style=for-the-badge)](#)

</div>

<br>

> ⚠️ **LEGAL DISCLAIMER:** This software is provided exclusively for security research, system testing, and educational purposes. The developer strictly does not endorse, promote, or condone any form of illegal activity, system abuse, or violation of any platform's terms of service. All actions taken and consequences arising from the use of this software are the sole responsibility of the user.

---

## ⚡ System Architecture

SIOUX BYPASSER is an enterprise-grade, highly advanced browser extension designed to intercept, manipulate, and evaluate payment gateway workflows in real-time. Unlike traditional standalone extensions, SIOUX operates on a **Distributed Cloud Architecture**:

* **Client-Side (MV3):** Executes aggressive DOM manipulation, CSP network stripping, and state machine automation directly within the victim's browser context.
* **Server-Side (Cloudflare Workers):** Manages real-time license validation (Premium/Trial), secure asset distribution, and payload routing via KV databases (`LICENSES_KV`, `SIOUX_ASSETS`).
* **3DS Relay Engine:** Employs an injected relay script (`inject-relay.js`) to extract and bypass 3D Secure endpoints seamlessly.

---

## 🛡️ Target Infrastructure

Engineered with specific DOM sensors and manipulation logic for a massive array of global payment processors and storefronts.

| Tier 1 Processors | Alternative Billing | Platform Stores |
| :--- | :--- | :--- |
| **Stripe** | Paddle | Steam |
| **Airwallex** | Xsolla | GOG |
| **Adyen** | NordPay | OpenAI |
| **Braintree** | HiPay | |
| **Checkout.com** | Smart Glocal | |
| **Square** | EdfaPay | |

---

## 🕸️ Tactical Capabilities

### 1. Advanced Network Manipulation
* **Brute-Force CSP Stripping:** Utilizes MV3 `declarativeNetRequest` rules to strip `Content-Security-Policy` headers directly at the network layer, preventing target platforms from blocking injected payloads.
* **Risk Evaluation Engine:** Built-in heuristics (`RiskEvaluations`) to calculate risk scores, determine risk bands, and output recommended actions before payload execution.

### 2. DOM Siege & Automation
* **SafeKey Hunter:** A relentless `MutationObserver` that scans and destroys 3D Secure/SafeKey DOM elements every 300 milliseconds to prevent checkout interruptions.
* **Stripe AutoClick FSM:** A Finite State Machine designed to automate checkout flows and intercept Amex sessions via simulated "Escape" keydown events.
* **Anti-Debugging:** Hijacks console methods to blind platform telemetry and error tracking.

### 3. Analytics & BIN Management
* **Live Operations Dashboard:** Real-time tracking of operations categorized into **Paid**, **LIVE**, **DEAD**, and **Decline** outcomes.
* **BIN Library Manager:** Built-in database for managing and deploying custom BIN lists, featuring pre-loaded read-only libraries (e.g., Ayden, VPN BINS, Stripe Auto Renewal).

---

## 🏗️ Installation & Deployment

SIOUX BYPASSER is designed for seamless distribution and rigorous testing environments. 

### Prerequisites
* Node.js (v18 or higher)
* Chromium-based browser or Firefox Developer Edition

### Development / Unpacked Testing

**For Firefox (Primary Testing Environment):**
The repository includes dedicated automation scripts to install the extension directly into your Firefox profile.
```bash
# Install to a specific Firefox profile
node install-firefox-profile-addon.mjs --profile-name "YourProfileName"
