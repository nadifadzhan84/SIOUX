<div align="center">

# 🦅 SIOUX BYPASSER
**Payment Siege Extension for Elite Gateway Exploitation**

[![Version](https://img.shields.io/badge/Version-1.9.4-blue.svg?style=for-the-badge)](#)
[![Manifest V3](https://img.shields.io/badge/Manifest-V3-success.svg?style=for-the-badge)](#)
[![Architecture](https://img.shields.io/badge/Architecture-Distributed_Cloud-orange.svg?style=for-the-badge)](#)
[![Runtime](https://img.shields.io/badge/Runtime-Firefox_142+-red.svg?style=for-the-badge)](#)

</div>

<br>

> ⚠️ **LEGAL DISCLAIMER:** This software is provided only for lawful testing, authorized security research, internal QA, and interoperability evaluation on systems, accounts, applications, or environments that you own or are explicitly permitted to assess. Unauthorized access, fraud, circumvention of security controls, violation of platform terms, or unlawful use is strictly prohibited.

SIOUX BYPASSER is an enterprise-grade, highly advanced browser extension designed to intercept, manipulate, and evaluate payment gateway workflows in real-time. Built on Manifest V3, it utilizes a sophisticated distributed architecture, combining aggressive DOM manipulation on the client side with a remote Cloudflare Worker backend for license management and 3DS relay routing.

---

## ⚡ Core Capabilities

### 🛡️ Universal Gateway Targeting
Engineered with specific sensors and manipulation logic for a massive array of global payment processors and storefronts, including:
* **Tier 1 Gateways:** Stripe, Airwallex, Adyen, Braintree, Checkout.com, Square.
* **Alternative Billing:** Paddle, Xsolla, NordPay, HiPay, Smart Glocal, EdfaPay.
* **Platform Stores:** Steam, GOG, OpenAI.

### 🕸️ Advanced Network Manipulation
* **CSP Stripping:** Utilizes brute-force `declarativeNetRequest` rules to strip `Content-Security-Policy` headers directly at the network layer, preventing target platforms from blocking injected payloads.
* **Risk Evaluation Engine:** Built-in heuristics (`RiskEvaluations`) to calculate risk scores, determine risk levels, and output recommended actions before payload execution.
* **SafeKey Hunter:** A relentless `MutationObserver` that scans and destroys 3D Secure/SafeKey DOM elements every 300 milliseconds to prevent checkout interruptions.
* **Stripe AutoClick FSM:** A Finite State Machine designed to automate checkout flows and intercept Amex sessions via simulated "Escape" keydown events.

### ☁️ Cloud-Backed Architecture
Unlike traditional standalone extensions, SIOUX uses a distributed service layer to support licensing, configuration delivery, and runtime coordination for authorized testing deployments.
* **Backend Services:** Uses a remote service layer for license validation, asset delivery, and server-backed extension state.
* **Relay Layer:** Includes companion runtime components to support workflow coordination for supported testing scenarios.

### 📊 Tactical Dashboard & BIN Management
* **Live Analytics:** Real-time tracking of operations categorized into Paid, LIVE, DEAD, and Decline outcomes.
* **BIN Library Manager:** Built-in database for managing and deploying custom BIN lists, including pre-loaded read-only libraries (Ayden, VPN BINS, Cursor, Stripe Auto Renewal).

---

## 🏗️ Architecture & Deployment

SIOUX BYPASSER is designed for seamless distribution and rigorous testing environments. 

### Infrastructure Stack
* **Client:** JavaScript (MV3), HTML, CSS.
* **Backend:** Cloudflare Workers + KV Storage.
* **Asset Distribution:** Optimized for a hybrid Worker + Google Drive architecture to serve extension updates dynamically.

### Installation (Development & Testing)

**Firefox minimum version:** `142.0`

#### Option A: Install from the Bundled XPI

If you just want to install the packaged Firefox build that is already included in this repo, use:

`dist/sioux-bypasser-v1.9.4.xpi`

Installation steps:

1. Open Firefox.
2. Open `about:addons`.
3. Click the gear icon, then choose **Install Add-on From File...**
4. Select:
   ```text
   dist/sioux-bypasser-v1.9.4.xpi
   ```
5. Confirm the installation prompt if Firefox allows the add-on.
6. After installation, click the SIOUX toolbar icon to open the main dashboard (`options.html`).

> **Important:** The bundled `sioux-bypasser-v1.9.4.xpi` in this repo is a packaged build, but it is not signed by Mozilla. Firefox install-from-file is intended for signed add-ons, and standard Firefox Release can reject unsigned packages. If Firefox rejects the file, use **Option B** below or test with Firefox Developer Edition, ESR, or Nightly.

#### Option B: Load Temporarily in Firefox

This is the safest local testing method when Firefox refuses the unsigned `.xpi`.

1. Open Firefox and visit `about:debugging#/runtime/this-firefox`.
2. Click **Load Temporary Add-on**.
3. Select `manifest.json` from the repository root.
4. Firefox will load the extension immediately.
5. Click the SIOUX toolbar icon to open the main dashboard (`options.html`).
6. After editing source files, return to `about:debugging` and click **Reload** on the add-on entry.

#### Option C: Install Into a Firefox Profile

Use this flow when you want a repeatable Firefox testing profile.

1. Ensure Node.js is installed.
2. Install project dependencies:
   ```bash
   npm install
   ```
3. List available Firefox profiles:
   ```bash
   npm run firefox:profiles:list
   ```
4. Install the extension into a selected profile:
   ```bash
   npm run firefox:install:profile -- --profile-name "YourProfileName"
   ```
5. If needed, you can target a profile directory directly:
   ```bash
   node scripts/install-firefox-profile-addon.mjs --profile-dir "C:\path\to\Firefox\Profiles\your-profile"
   ```
6. Launch Firefox with that profile, then click the SIOUX toolbar icon to open the dashboard.

### Using SIOUX in Firefox

After the add-on is loaded in Firefox:

1. Click the SIOUX extension icon in the Firefox toolbar.
2. The icon opens the main configuration page (`options.html`).
3. Open the **License Key** section, enter your key, then click **Verify & Activate**.
4. Add BINs in the **Configuration** section.
5. If needed, configure a proxy in **Advanced** using **Primary Proxy** or the proxy rotation list.
6. Open a supported checkout page and refresh the tab after changing settings so the latest configuration is applied.
7. Monitor the **Logs** panel for runtime activity, gateway responses, and risk output.

If license activation fails while a proxy is active, disable the proxy first, activate the license, then apply the proxy again.

### Packaging for Firefox

If you already use the bundled `dist/sioux-bypasser-v1.9.4.xpi`, you do not need to rebuild anything.

To generate a new Firefox package:

```bash
npm run build:xpi
```

The packaged file will be created in `dist/sioux-bypasser-v<version>.xpi`.

---

## LICENSE KEY

<details>
<summary><strong>Authorized Testing Use Only</strong></summary>

Don’t forget to download the LICENSE KEY on the right to use the full version.
---

## Disclaimer

<details>
<summary><strong>Authorized Testing Use Only</strong></summary>

This software is provided only for lawful testing, authorized security research, internal QA, and interoperability evaluation on systems, accounts, applications, or environments that you own or are explicitly permitted to assess.

It must not be used for unauthorized access, circumvention of security controls, fraud, violation of platform terms, unauthorized data collection, or any unlawful or harmful activity.

All actions taken with this software and any resulting consequences are solely the user's responsibility. This product is provided on an "as is" basis without warranties of any kind, and the developer is not liable for misuse, loss, service disruption, or legal consequences arising from unauthorized use.

If you do not agree to these terms, do not use this software. This disclaimer does not legalize unauthorized activity and does not constitute legal advice.

</details>
