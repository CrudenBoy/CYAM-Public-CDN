# Context Knowledge: CYAM Admin Console AI Engines

This document provides authoritative knowledge for the CYAM Help Cartel Chatbot to assist non-technical Admins configuring local AI (Ollama) and cloud APIs (OpenRouter).

## 1. Ollama is now a Graphical Application
As of late 2025, Ollama is no longer just a silent background terminal application. It has a full Graphical User Interface (GUI) chat app.

### Pre-flight System Requirements:
- **Windows:** Windows 10 version 22H2 or newer (Home or Pro). GPU users require NVIDIA driver 452.39+ or AMD Radeon.
- **macOS:** macOS 14 Sonoma or newer. Apple M-series chip (CPU + GPU) or Intel x86 (CPU-only).
- **Disk Space:** Minimum 4 GB for binary; 2–100+ GB additional for models.

### macOS Installation Flow Recap:
**CRITICAL CLARIFICATION:** Do not extract a zip file!
1. Download the macOS **.dmg** file from `https://ollama.com/download/Ollama.dmg`.
2. Double-click to mount the `.dmg` file.
3. Drag the `Ollama` app icon into the **Applications** folder shortcut.
4. Double-click it in Applications. macOS Gatekeeper asks: *"Ollama is an app downloaded from the Internet..."* -> Admin clicks **Open**.
5. Ollama prompts to install the CLI tool into `/usr/local/bin` -> Admin clicks **Install** and enters their **Mac Password** (or Touch ID).
6. The Ollama App interface will then launch automatically on the desktop.
7. *Verification:* A small Llama icon will appear in the macOS top menu bar.

### Windows Installation Flow Recap:
1. Run the `OllamaSetup.exe`.
2. Click **Install**.
3. Follow the wizard. The Ollama App interface will launch automatically.
4. *Verification:* The app runs in the background and is available via the `ollama` command in PowerShell.

## 2. Model Downloads & CYAM Recommendations (No Terminal Needed)
Admins do not need to use Terminal, Command Prompt, or any CYAM web integration to download local models. 
1. In the top area of the Ollama App chat window, click the model selector dropdown.
2. A search bar will appear `Find model...`
3. Type the CYAM-recommended model tag and click the download icon next to it.
4. Wait for the progress bar to complete inside the Ollama App.

**🏆 CYAM Recommended Models (March 2026):**
- **TOP PICK: `qwen3:4b`** — Best all-round choice. Only ~3–4 GB RAM. 128K context window. Built-in "Thinking" mode. 119 languages. [ollama.com/library/qwen3:4b](https://ollama.com/library/qwen3:4b)
- **RUNNER-UP: `gemma3:4b`** — Best for documents with images/diagrams (multimodal). 128K context. 82.3% DocVQA score. [ollama.com/library/gemma3:4b](https://ollama.com/library/gemma3:4b)

**Hardware Sizing:**
- **8 GB RAM:** ✅ Both `qwen3:4b` and `gemma3:4b` run smoothly.
- **16 GB RAM:** ✅ Plenty of headroom. Can also try larger 7B–9B models.
- **24 GB+ RAM:** ✅ Can handle 12B–32B models for maximum quality.

**Fallback: Free Cloud Offloading**
If the Admin's computer lacks sufficient RAM or disk space to install Ollama or download a model, advise them to **skip the local installation completely**. Instead, they can configure CYAM to offload simple background tasks to a **Free OpenRouter Model** (e.g., `openrouter/free` or `google/gemma-3-8b-it:free`). This prevents hidden background tasks from consuming paid cloud credits while avoiding hardware bottlenecks on older machines.

## 3. Storage Drives (OLLAMA_MODELS)
If an Admin states their C: drive or immediate disk is full and they cannot pull local models:

**Windows Step-by-Step:**
1. Open Windows Control Panel or Settings -> Search for **environment variables**.
2. Click **Edit environment variables for your account**.
3. Create a new User Variable named `OLLAMA_MODELS` and point it to a new drive folder (e.g., `D:\OllamaModels`).
4. Click OK/Apply, quit Ollama from the system tray, and relaunch it.

**macOS Step-by-Step:**
Models are stored at `~/.ollama/models` by default. Add `OLLAMA_MODELS=/your/path` to the shell profile (`.zshrc` or `.bash_profile`) and restart Ollama.

## 4. OpenRouter API Keys & Credits

CYAM routes heavy tasks to OpenRouter safely using your configured API key. OpenRouter offers three distinct access paths, each with different setup requirements and cost structures.

**CRITICAL: No credit card is required to get started.** You can create an OpenRouter account and generate an API key completely free, with immediate access to high-quality open-source models.

### Path A: Free Tier Setup (No Payment Required)

**Understanding Free Tier Access:**

Free-tier users have immediate access to a rotating selection of community and open-source models with a rate limit of **50 requests per day**. This limit increases to **1,000 requests per day** once you add at least $10 in credits to your account, even if you continue using only free models. The free tier provides access to capable models that are suitable for development, testing, and lightweight production applications.

**Step-by-Step Free Tier Setup:**

1. **Create Your OpenRouter Account:** Navigate to `https://openrouter.ai/auth` and sign up using your email, Google account, or GitHub account. Email verification may be required for security purposes.

2. **Generate Your API Key:** Once logged in, visit `https://openrouter.ai/settings/keys`. Click the **"Create Key"** button in the API Keys section.

3. **Name Your Key Descriptively:** Provide a clear name for your key such as **`CYAM-App`**, **`My-Business-AI`**, or **`Development-Testing`**. This helps you identify keys later if you create multiple keys for different projects or environments.

4. **Copy and Secure Your Key:** After clicking "Create", your API key will be displayed once. Copy it immediately and store it securely. OpenRouter will not show the full key again for security reasons.

5. **Configure CYAM:** Return to the CYAM Dashboard and paste your API key into the OpenRouter configuration field during Task 3.

**Finding and Using Free Models:**

To browse available free models, visit `https://openrouter.ai/models?q=free` or use the model catalog with the "Free" filter enabled. As of March 2026, reliable free models include:

- **`openrouter/free`** — A special model ID that automatically routes to the best available free model at the time of your request
- **`meta-llama/llama-3.3-70b-instruct:free`** — High-quality instruction-following model with 128K context window
- **`qwen/qwen-3.5-7b-instruct:free`** — Efficient multilingual model with strong reasoning capabilities
- **`google/gemma-2-9b-it:free`** — Instruction-tuned model from Google with good performance
- **`mistralai/mistral-7b-instruct:free`** — Fast, capable model for general tasks

Free model availability may change over time as OpenRouter partners with different providers. Check the models page regularly for current offerings and new additions to the free tier.

### Path B: Premium Credits Setup

**Understanding OpenRouter's Credit System:**

OpenRouter operates on a prepaid credit system with no subscriptions or recurring charges. Credits are consumed on a pay-as-you-go basis, with pricing that **matches the per-token rates set by each model provider**. OpenRouter does **not** apply a per-token markup to model usage. The only fee is a **one-time transaction fee of 5.5%** when purchasing credits via credit or debit card (5% for cryptocurrency payments), with a minimum fee of approximately **$0.80 per transaction**.

**Detailed Credit Purchase Process:**

1. **Navigate to Credits Page:** Visit `https://openrouter.ai/settings/credits` while logged into your OpenRouter account.

2. **Click "Add Credits":** Look for the prominent "Buy Credits" or "Add Credits" button near the top of the page.

3. **Enter Purchase Amount:** The minimum credit purchase is **$5.00**. Enter your desired amount. Common purchase amounts are $10, $25, $50, or $100. Remember that a 5.5% transaction fee will be added at checkout (e.g., $10 in credits costs $10.55 total).

4. **Select Payment Method:** OpenRouter accepts multiple payment options:
   - Credit or debit cards (Visa, Mastercard, American Express)
   - Google Pay
   - Amazon Pay
   - Cash App
   - USDC cryptocurrency (lower 5% transaction fee)

5. **Complete Payment:** Follow the payment provider's checkout flow. Your credits will be added to your account immediately upon successful payment.

6. **Verify Credit Balance:** After payment, your credit balance appears at the top of the settings page and in the main dashboard.

**How Credits Are Consumed:**

When you make an API request to a paid model, OpenRouter calculates the cost based on the exact provider pricing:
- **Input tokens** (prompt) × model's input price per token
- **Output tokens** (completion) × model's output price per token

**Example Cost Calculation:**
If `anthropic/claude-3-5-sonnet-20241022` costs $3.00 per million input tokens and $15.00 per million output tokens, a request with 1,000 input tokens and 500 output tokens would cost:

$$\text{Cost} = (1,000 \times \frac{\$3.00}{1,000,000}) + (500 \times \frac{\$15.00}{1,000,000}) = \$0.003 + \$0.0075 = \$0.0105$$

This pricing matches Anthropic's official developer rates exactly—OpenRouter adds no markup beyond the initial 5.5% credit purchase fee.

**Credit Management Details:**

- **Expiration Policy:** Credits remain valid for **365 days** from the date of purchase
- **Usage Tracking:** Monitor your credit consumption at `https://openrouter.ai/activity`
- **Auto-Reload (Optional):** Enable automatic credit reloading when your balance falls below a specified threshold
- **No Refunds:** OpenRouter does not offer refunds on credit purchases, as credits are immediately available for use

### Path C: Bring Your Own Key (BYOK) Setup

**Understanding BYOK Pricing Structure:**

When you configure BYOK, OpenRouter routes requests directly to the provider using your personal API key. You are billed by the provider at their standard developer rates. OpenRouter provides **1 million free BYOK requests per month**—after exceeding this threshold, OpenRouter charges a **5% usage fee** on additional BYOK requests, deducted from your OpenRouter credit balance (not your provider balance). Enterprise accounts may receive unlimited free BYOK requests.

**BYOK Configuration Process:**

1. **Navigate to BYOK Settings:** Visit `https://openrouter.ai/workspaces/default/byok` while logged into OpenRouter.

2. **Select Your Provider:** Click the **"Add Provider Key"** button. You'll see supported providers including OpenAI, Anthropic, Google, Mistral AI, and Cohere.

3. **Obtain Provider API Keys:** Before configuring BYOK, you need valid API keys from each provider:

   **OpenAI:**
   - Visit `https://platform.openai.com/api-keys`
   - Click **"Create new secret key"**
   - Name your key (e.g., `OpenRouter-BYOK`)
   - Copy the key immediately (starts with `sk-`)
   - Ensure valid payment method at `https://platform.openai.com/settings/organization/billing`

   **Anthropic:**
   - Visit `https://console.anthropic.com/settings/keys`
   - Click **"Create Key"**
   - Name your key appropriately
   - Copy the key (starts with `sk-ant-`)
   - Add payment method at `https://console.anthropic.com/settings/billing`

   **Google AI (Gemini):**
   - Visit `https://aistudio.google.com/app/apikey`
   - Click **"Create API Key"**
   - Select or create a Google Cloud project
   - Copy the generated key
   - Ensure billing is enabled in Google Cloud Console

   **Mistral AI:**
   - Visit `https://console.mistral.ai/api-keys`
   - Generate new API key
   - Copy and secure the key

   **Cohere:**
   - Visit `https://dashboard.cohere.com/api-keys`
   - Generate production API key
   - Copy the key securely

4. **Configure Keys in OpenRouter:** Back in OpenRouter's BYOK settings, select the provider, paste your API key into the secure input field, and click **"Save"**.

5. **Verify Key Status:** OpenRouter will test the key immediately. A green checkmark indicates successful verification.

**BYOK Cost Example:**
- First 1,000,000 BYOK requests per month: **$0 OpenRouter fee** (you still pay the provider directly)
- Requests 1,000,001 and beyond: **5% OpenRouter fee** (deducted from your OpenRouter credits) + direct provider billing

## 5. AI Model Routing Table
CYAM ships a pre-configured **AI Model Routing Table** (`AI Model Routing Table.csv`) that maps each platform function to the best AI model. Users do NOT need AI expertise — the defaults are production-ready.

**Key Concepts:**
- **Primary Model:** The first-choice model for each function. Some are free (e.g., `qwen/qwen-3.5-7b-instruct:free`), most are paid.
- **Fallback / Escalation Model:** A backup used if the primary fails OR when an escalation trigger fires.
- **Escalation Trigger:** The condition that switches from Primary → Fallback. Most functions use standard failover (timeout/error). The Help & Context Chatbot uses a special trigger: `ESCALATE_TO_WEB`.

**The ESCALATE_TO_WEB Pattern:**
1. User asks the Help & Context Chatbot a question.
2. CYAM sends the question + the local `Context_Knowledge.md` docs to the FREE `qwen/qwen-3.5-7b-instruct` model.
3. If the answer is in the docs → respond immediately (zero cost).
4. If the answer is NOT in the docs → Qwen replies with exactly: `ESCALATE_TO_WEB`.
5. CYAM intercepts this trigger and re-routes the same question to `x-ai/grok-4.1-fast` (paid, web-capable).
6. Grok searches the live web and returns an answer.

**Customising Models:**
- Users can change any Primary or Fallback model via the Admin Console dropdowns.
- The CSV file can also be updated directly (uploaded via CYAM Marketplace or edited locally).
- Changes take effect immediately after clicking "Save Configuration".

## 6. Verification Testing Protocols (Cloud Only)
To comply with strict Google Workspace Marketplace security standards (Tier 1 CASA readiness), the CYAM platform does not connect to the local computer network to verify Ollama. The Admin provides visual confirmation by completing the download in the Ollama App and toggling the configuration in CYAM.

**OpenRouter Verification:** CYAM automatically executes a **Test Connection protocol** by sending a tiny test generation (`"Say this is a test"`) to the selected cloud model. 
*CRITICAL TIER 1 DETAIL:* This test is executed securely **client-side directly from the user's web browser**. This ensures CYAM avoids requesting invasive server-side external network permissions (`script.external_request`) from the user's Google Workspace! A green "Verified & Active" badge only appears upon an HTTP 200 success response. If it fails, they will see the direct HTTP error code to debug.

## 7. Chrome Split-Screen for CYAM + OpenRouter (Task 3)

During Task 3, the Admin must work simultaneously in the CYAM Dashboard (left) and the OpenRouter platform (right). Chrome's built-in **Split View** makes this seamless. The Help Carousel in the CYAM Dashboard includes 7 annotated screenshots walking through this process.

### Part 1: Add "Open in Split View" to the Chrome toolbar

1. **Customize Chrome:** Open Chrome's menu (⋮), go to **More Tools → Customize Chrome**. This opens the Chrome customization panel where toolbar buttons can be turned on or off.
2. **Open Toolbar settings:** Inside the Customize Chrome panel, click **Toolbar**. This takes you to the list of buttons that can appear in Chrome's toolbar.
3. **Enable Split View:** In the Toolbar section, turn on the toggle for **Open In Split View**. Once enabled, Chrome shows the Split View control directly in the toolbar for quick access.

### Part 2: Use Chrome Split View with CYAM + OpenRouter

4. **Open two tabs:** Keep the CYAM Dashboard open in one tab. Open a second tab and navigate to `https://openrouter.ai/settings/keys`. If not signed in, OpenRouter will redirect to its sign-in page first.
5. **Start Split View:** Right-click the OpenRouter tab and choose **"New split view with current tab"**. Alternatively, click the Split View button you just added to the toolbar, or drag a tab toward the edge of the Chrome window until the split target line appears.
6. **Position the panels:** Place the CYAM Dashboard on the **left** and OpenRouter on the **right**. If Chrome puts them in the wrong order, use Chrome's split-view controls to swap, or separate and restart with CYAM active first. The active panel has a thicker border.
7. **Resize and exit:** Drag the center divider left or right until both CYAM and OpenRouter are easy to read. When finished, exit Split View by separating the views back into regular tabs or closing one side.

### Key OpenRouter Pages the Admin will visit:
- **Authorization:** `https://openrouter.ai/auth`
- **API Key Settings:** `https://openrouter.ai/settings/keys`
- **Add Credits:** `https://openrouter.ai/settings/credits`
- **BYOK:** `https://openrouter.ai/workspaces/default/byok`

## 8. Bring Your Own Key (BYOK) in OpenRouter

BYOK allows Admins to attach their own API keys from providers like OpenAI, Anthropic, Google, Mistral, or Cohere directly inside OpenRouter's workspace—**not inside CYAM**. This creates a direct billing relationship with the provider while maintaining OpenRouter's unified API interface.

### Key Facts:

- **Model slugs are IDENTICAL.** `openai/gpt-4o` is the same slug whether funded via BYOK, credits, or free tier. No special prefixes or changes needed in the CYAM Routing Table.

- **BYOK takes automatic priority.** When a BYOK key is configured for a provider, OpenRouter uses it for matching models automatically. No CYAM configuration change needed.

- **1 Million Free BYOK Requests Monthly.** OpenRouter provides 1,000,000 free BYOK requests per month. After exceeding this threshold, a 5% usage fee applies, deducted from your OpenRouter credit balance.

- **Credits remain as fallback.** Your OpenRouter credits are preserved for non-BYOK providers and for the 5% BYOK fee after exceeding the free threshold.

- **API does NOT expose BYOK status.** The `GET /api/v1/models` endpoint returns the global model catalog with standard pricing. It does not indicate which models are BYOK-enabled for a specific user for privacy and security reasons.

- **BYOK-Compatible Providers (as of March 2026):** OpenAI, Anthropic, Google AI, Mistral AI, Cohere, Amazon Bedrock (enterprise), Azure OpenAI (enterprise).

### BYOK Cost Tracking:

BYOK requests bypass OpenRouter's usage dashboard for provider billing. Admins must track costs directly:

- **OpenAI:** Check usage at `https://platform.openai.com/usage`
- **Anthropic:** Check usage at `https://console.anthropic.com/settings/usage`
- **Google:** Check usage in Google Cloud Console → Billing → Reports
- **Mistral:** Check usage at `https://console.mistral.ai/usage`
- **Cohere:** Check usage at `https://dashboard.cohere.com/billing`

OpenRouter credits are only consumed for:
1. The 5% BYOK fee (after exceeding 1M requests/month)
2. Models from providers where you haven't configured BYOK keys

### BYOK Setup Steps:

1. Visit `https://openrouter.ai/workspaces/default/byok`
2. Click **"Add Provider Key"** and select your provider
3. Obtain API keys from each provider (see detailed instructions in Section 4, Path C)
4. Paste your provider API key into OpenRouter's secure input field
5. Click **"Save"** and verify the green checkmark appears
6. Return to CYAM—the Routing Table automatically benefits from BYOK routing
7. Monitor usage through each provider's own dashboard

### Common Troubleshooting:

| Symptom | Cause | Resolution |
|---|---|---|
| BYOK model suddenly fails | Expired payment method on provider account | Update billing at provider dashboard |
| Requests using credits despite BYOK | BYOK key removed, expired, or rate-limited | Re-add key at OpenRouter BYOK page |
| "Insufficient credits" error with BYOK | Exceeded 1M free BYOK requests and no OpenRouter credits for 5% fee | Add credits to OpenRouter account |
| Key verification fails | Invalid key format or provider API issues | Regenerate key at provider dashboard |
| Rate limit errors | Hit provider-specific rate limits | Upgrade plan with provider |

## 9. Access Path Comparison (Task 3, Step 3.5)

| Criterion | Path A (Free) | Path B (Credits) | Path C (BYOK) |
|---|---|---|---|
| **Upfront Cost** | Free—no payment required | Minimum $5 credit purchase + 5.5% transaction fee ($5.28 total) | Free to configure; requires provider account with payment method |
| **Ongoing Costs** | Zero | Per-token usage at provider rates; no markup beyond one-time 5.5% credit purchase fee | Direct provider billing + 5% OpenRouter fee only after 1M requests/month |
| **Model Quality** | Community/open-source (Llama 3.3 70B, Qwen 3.5 7B, Gemma 2 9B)—suitable for testing and lightweight production | Full frontier access (GPT-4o, Claude 3.5 Sonnet, Gemini Pro) | Identical premium models as Path B |
| **Setup Effort** | Minimal—create account, generate key (5 minutes) | Low—credit card payment after account creation (5-10 minutes) | Moderate—obtain provider keys, configure each provider (15-30 minutes) |
| **Billing Complexity** | None | Single prepaid balance to monitor in OpenRouter dashboard | Separate invoices from each provider + OpenRouter fee tracking after 1M requests |
| **Rate Limits** | 50 requests/day (1,000/day with $10+ credits purchased) | Unlimited (subject to credit balance and model-specific limits) | Provider-specific limits (typically much higher than free tier) |
| **Best For** | Development, testing, POC, education, low-volume production | Production apps with moderate usage, simplified billing, no existing provider relationships | High-volume apps (>1M requests/month), existing provider contracts, enterprise compliance |

**Guidance:** Start with Path A to validate integration and test your application logic. Upgrade to Path B when deploying premium models for moderate usage volumes. Choose Path C for high-volume production applications or when you have existing enterprise relationships with providers. You can switch paths at any time—Task 4's routing table automatically reflects available models based on your current configuration.

## 10. Human-Facing Instructions for CYAM Dashboard

**Step 1 — Understanding Bring Your Own Key (BYOK):** OpenRouter's BYOK feature allows you to connect your personal API keys from major providers like OpenAI, Anthropic, and Google directly to your OpenRouter workspace. When you configure BYOK, your CYAM Platform continues to function identically, but the billing relationship changes significantly. Instead of deducting costs from your OpenRouter prepaid credits, the token usage is billed directly to you by the provider at their standard developer rates. OpenRouter provides your first 1 million BYOK requests each month completely free, and only charges a small 5% fee on requests beyond that threshold. Your Model Routing Table in CYAM works exactly the same way—you still select models using standard names like `openai/gpt-4o`—but OpenRouter automatically routes these requests through your personal keys when available.

**Step 2 — How BYOK Priority and Routing Works:** Once you add a provider key in OpenRouter's BYOK settings, it automatically takes priority over OpenRouter credits for models from that provider. You don't need to make any changes in CYAM's interface or configuration. When you select `openai/gpt-4o` in your Routing Table and you have an OpenAI BYOK key configured, OpenRouter will automatically use your key for those requests. If your BYOK key encounters issues like rate limits or billing problems, OpenRouter may fall back to using your credits depending on the error type. This automatic routing means you can have BYOK configured for some providers (like OpenAI for high-volume usage) while still using OpenRouter credits for others (like community models), giving you flexible cost management across different AI providers.

**Step 3 — Identifying BYOK-Compatible Models:** BYOK support is available for major commercial providers including OpenAI, Anthropic, Google, Mistral, and Cohere. In your Model Routing Table, look for models from these established providers—they will show a key icon (🔑) indicating BYOK compatibility. Community models, open-source models hosted by third parties, or specialized fine-tuned models generally require OpenRouter credits and cannot be routed through personal API keys. When selecting models for high-volume functions like your Main Chat, prioritizing BYOK-compatible models from major providers can significantly reduce your operational costs while maintaining high-quality AI responses, especially once you exceed the 1 million free BYOK requests per month threshold.

**Step 4 — Managing BYOK Configuration and Cost Tracking:** To set up BYOK, visit OpenRouter's dedicated BYOK settings page at `https://openrouter.ai/workspaces/default/byok` while logged into the same account you connected to CYAM during OAuth authorization. There you can securely add API keys for multiple providers simultaneously—OpenRouter will intelligently route each request to the appropriate key based on your model selections. Since BYOK requests bypass OpenRouter's usage dashboard for provider billing, you must track costs directly through each provider's dashboard: OpenAI usage at `platform.openai.com/usage`, Anthropic at `console.anthropic.com/settings/usage`, and Google in the Cloud Console. Remember that after your first million BYOK requests each month, you'll need a small OpenRouter credit balance to cover the 5% usage fee, so monitor both your provider costs and your OpenRouter credit consumption to maintain uninterrupted service.
