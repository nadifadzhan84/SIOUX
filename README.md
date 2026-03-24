# 🦅 SIOUX BYPASSER v1.9.4

**Payment Siege Extension for Elite Gateway Exploitation**

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
Unlike traditional standalone extensions, SIOUX operates with a distributed backend:
* **Worker Backend:** Integrates with Cloudflare Workers (`worker.js`) via KV databases (`LICENSES_KV`, `SIOUX_ASSETS`) for real-time license validation (Premium/Trial).
* **3DS Relay:** Employs an injected relay script (`inject-relay.js`) to extract and route 3DS endpoints seamlessly.

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

#### Option A: Load Temporarily in Firefox

This is the fastest way to test the extension locally in Firefox.

1. Open Firefox and visit `about:debugging#/runtime/this-firefox`.
2. Click **Load Temporary Add-on**.
3. Select `manifest.json` from the repository root.
4. Firefox will load the extension immediately.
5. Click the SIOUX toolbar icon to open the main dashboard (`options.html`).
6. After editing source files, return to `about:debugging` and click **Reload** on the add-on entry.

#### Option B: Install Into a Firefox Profile

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

> **Note:** Firefox release builds still require a signed add-on for persistent installs. For unsigned local testing, use Firefox Developer Edition, ESR, or Nightly, or use the temporary add-on flow above.

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

To build a Firefox package:

```bash
npm run build:xpi
```

The packaged file will be created in `dist/sioux-bypasser-v<version>.xpi`.
