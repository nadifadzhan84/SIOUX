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

**For Firefox (Primary Testing Environment):**
The repository includes dedicated automation scripts to install the extension directly into your Firefox profile.
1. Ensure you have Node.js installed.
2. Run the Firefox profile installer:
   ```bash
   node install-firefox-profile-addon.mjs --profile-name "YourProfileName"
