---
spec_id: "admin-console-ai-engines"
spec_version: "1.0"
generated_by: "CYAM_Spec_Designer"
generated_date: "2026-03-18"
category: "Admin Console"
---

# Specification: Admin Console AI Engines

## Level 1: Category
* **Category:** Admin Console
* **Permissions:** Restricted strictly to `User_Signups.Role=Admin`.

---

> **📋 Organizational Protocol**
> If you are operating within an organization, your first action is to
> diplomatically contact your ICT department to inform them of the
> actions you are about to take regarding configuring AI engines and local LLMs.

---

## Level 2: Install Local LLM (Ollama)
**Goal:** Guide the non-developer Admin through a one-time "install and forget" setup for local infrastructure, utilizing the native Ollama GUI.

> **Hardware limitations?** If your computer does not meet the minimum requirements below (or you lack disk space), you can **skip this entire workflow** and use the **"Free Cloud Offloading"** fallback in Workflow 2 to handle simple background tasks without consuming paid credits.

### Level 3: Task 1 — Download & Install Ollama

#### Level 4: Steps

1. In the **CYAM Admin Console**, select your operating system (Windows or macOS).
2. The UI displays a direct download button for the official Ollama installer.
   * **Pre-flight: System Requirements Check**
     Before downloading, confirm your machine meets minimum requirements:
     * **Windows:** Windows 10 version 22H2 or newer (Home or Pro). If you have a GPU: NVIDIA driver 452.39+ or AMD Radeon driver from [amd.com/en/support](https://www.amd.com/en/support).
     * **macOS:** macOS 14 Sonoma or newer. Apple M-series chip (CPU + GPU acceleration) or Intel x86 (CPU-only inference, slower).
     * **Disk Space (Both):** 4 GB minimum for the Ollama binary; an additional 2–100+ GB for models (varies by model size).
3. Perform the OS-specific installation.
[OS:Windows]
   * **Windows:**
     1. Locate the downloaded `OllamaSetup.exe` file in your Downloads folder and double-click it to launch the installer.
     2. Windows SmartScreen may display a warning: *"Windows protected your PC."* Click **"More info"** and then **"Run anyway"**.
     3. Click **"Install"** to begin the setup wizard. *(No Administrator rights are required — Ollama installs into your user account by default.)*
     4. Wait for the installation progress bar to complete. This typically takes 30–60 seconds.
     5. The new **Ollama App** (chat GUI) will launch automatically when setup completes. It also starts as a background service, making the `ollama` command available in PowerShell, CMD, and Windows Terminal.
     6. A small **Ollama icon** will appear in the Windows system tray (bottom-right corner by the clock), confirming the background service is running.
     7. **Verify the install:** Open PowerShell and type `ollama --version`. A version string confirms a successful install.

   > **🤖 Agent Automation**:
   > "Download the official Ollama Windows installer from https://ollama.com/download/OllamaSetup.exe and silence the install."
[/OS:Windows]

[OS:macOS]
   * **macOS:**
     1. Double-click the downloaded **Ollama.dmg** file to mount the disk image. A Finder window will open showing the Ollama app icon.
     2. In the Finder window that opens, drag the **Ollama** app icon into the **Applications** folder shortcut shown alongside it.
     3. Go to your **Applications** folder and double-click **Ollama** to open it.
     4. macOS Gatekeeper may display a warning: *"Ollama is an app downloaded from the Internet. Are you sure you want to open it?"* Click **Open**.
     5. On first launch, Ollama checks whether the `ollama` command-line tool exists in your PATH. If not found, it will prompt: *"Ollama requires a command-line tool to be installed in /usr/local/bin."* Click **Install** and authenticate with your **Mac Password** or **Touch ID** when prompted.
     6. The new **Ollama App** (GUI chat interface) will appear in your menu bar and desktop. *(A llama icon appears in the macOS menu bar to confirm it is running.)*
     7. **Verify the install:** Open Terminal and type `ollama --version`. A version string confirms a successful install.

   > **🤖 Agent Automation**:
   > "Download the Ollama macOS disk image from https://ollama.com/download/Ollama.dmg, mount it, copy Ollama.app to /Applications, and launch it."
[/OS:macOS]

##### Level 5: Help & Context

**Step 1 — OS Selection:** Choose your operating system (Windows or macOS) from the CYAM Admin Console to see the correct download link and installation steps.

**Step 2 — System Requirements:** Before downloading, verify your machine meets minimum requirements — Windows 10 22H2+ or macOS 14 Sonoma+, with at least 4 GB free disk space for the Ollama binary.

**Step 3 — Installation:** Follow the OS-specific installer steps. On Windows, handle SmartScreen warnings; on macOS, handle Gatekeeper prompts and CLI tool installation.

* **Carousel Item 1:** Task 1, Step 3: Windows Installation — Locate the downloaded OllamaSetup.exe, handle the SmartScreen warning, click Install, and verify via the system tray icon.
  (Media: `step3_win_installation.png`)
* **Carousel Item 2:** Task 1, Step 3: macOS Installation — Mount the disk image and drag Ollama to your Applications folder shortcut. Accept the Gatekeeper security prompt, and click Install for the CLI tool.
  (Media: `step3_mac_installation.png`)
* **Carousel Item 3:** Task 1, Step 3: macOS Verification — The Ollama llama icon will appear in the top menu bar, confirming the background service is running.
  (Media: `step3b_mac_menubar.png`)
* **Chatbot Note:** Assist Admins with specific OS installation nuances for Ollama ensuring they mount .dmg on mac and handle SmartScreen on Windows.

---

### Level 3: Task 2 — Pull Local Models (via Ollama GUI)

#### Level 4: Steps

1. Open the **Ollama App** on your computer. You will see a chat interface with a text input area.
2. In the top area of the app, click the **Model Dropdown menu** (it may say `Find model...` or display the name of a currently loaded model, such as a default cloud model).
3. In the search bar that appears, type the CYAM-recommended model tag.
   * **🏆 CYAM Recommended Models (March 2026):**
     * **TOP PICK: `qwen3:4b`** — Best all-round local model. Only ~3–4 GB RAM needed. 128K token context window. Built-in "Thinking" mode for deep reasoning. 119 languages supported. Excellent instruction-following. [ollama.com/library/qwen3:4b](https://ollama.com/library/qwen3:4b)
     * **RUNNER-UP: `gemma3:4b`** — Best if your documents contain images or diagrams (multimodal). 128K context window. Strong document understanding (82.3% DocVQA score). [ollama.com/library/gemma3:4b](https://ollama.com/library/gemma3:4b)
   * **Hardware Sizing Guide:** Both recommended models run on virtually any modern computer:
     * **8 GB RAM:** ✅ Both `qwen3:4b` and `gemma3:4b` run smoothly (only ~3–4 GB needed).
     * **16 GB RAM:** ✅ Plenty of headroom. Can also try larger 7B–9B models if desired.
     * **24 GB+ RAM:** ✅ Can handle 12B–32B parameter models for maximum quality.
     Browse the full model library at [ollama.com/library](https://ollama.com/library).
4. Locate the specific model in the results list and click the **Download icon** (↓ arrow) next to it to begin the download.
5. Wait for the download to complete within the Ollama App. A progress indicator will show the download status. `qwen3:4b` is approximately 2.6 GB.
   * **CLI Alternative:** If you prefer or the GUI download fails, you can also pull a model via terminal: `ollama pull qwen3:4b`. This is equivalent to using the GUI download.
6. Return to the **CYAM Admin Console** web browser window to configure your cloud routing.

##### Level 5: Help & Context

**Steps 1-2 — Open Ollama & Find Model:** Launch the Ollama App on your computer and click the Model Dropdown at the top of the chat interface to search for models.

**Step 3 — Model Selection:** Type the CYAM-recommended model tag (e.g., `qwen3:4b`). The recommended models only require 3–4 GB of RAM and run on virtually any modern computer.

**Steps 4-5 — Download & Wait:** Click the download arrow next to the model and wait for the progress bar to complete. The recommended `qwen3:4b` model is approximately 2.6 GB.

* **Carousel Item 1:** Task 2, Step 2: Inside the Ollama App, locate the model dropdown at the top of the chat interface.
  (Media: `step5_ollama_gui_dropdown.png`)
* **Carousel Item 2:** Task 2, Step 4: Search for your desired CYAM-approved model and click the download arrow icon directly in the UI.
  (Media: `step6_ollama_download_model.png`)
* **Carousel Item 3:** Task 2, Step 3: Model Naming — Ollama models use a name:tag format. If you enter a name without a tag, Ollama defaults to the recommended parameter count.
  (Media: `step6b_ollama_model_tags.png`)
* **Chatbot Note:** Rely purely on visual instructions for downloading models within the new Ollama GUI. Guidance on how to change the default storage drive using the `OLLAMA_MODELS` environment variable can be provided.

---

## Level 2: Select LLMs for Workflow Tasks
**Goal:** Link cloud billing and map specific models (Local or Cloud) to distinct CYAM platform functions.

### Level 3: Task 1 — Connect OpenRouter (Cloud BYOK)

#### Level 4: Steps

1. In the CYAM Admin Console, click the **"Authorize OpenRouter"** OAuth button.
2. CYAM's backend generates the necessary cryptographic PKCE challenges (a `code_verifier` and SHA-256 `code_challenge`) and safely redirects you to `openrouter.ai/auth`.
   * **What is PKCE?** Proof Key for Code Exchange (PKCE) is a security extension to the standard OAuth 2.0 authorization flow. It ensures that only the CYAM application that initiated the request can exchange the returned authorization code for an API key — preventing interception attacks. [Read more at OpenRouter Docs](https://openrouter.ai/docs/guides/overview/auth/oauth).
3. Log into your OpenRouter account (or create one — it's free).
   * **No credit card is required at this stage.** You can immediately use OpenRouter's **free models** (like Llama 3.3 70B Instruct or GPT-4o-mini on select providers) without adding any payment method. Free models are rate-limited to **50 requests/day**.
   * You can also use the special model ID `openrouter/free` which automatically routes your requests to currently available free models.
4. After signing in, you will see a **"Get API Key"** button. Click it. You will be prompted to:
   * **Name your key:** Use a descriptive, recognizable name (e.g., `CYAM-App`, `My-Business-AI`). This helps you identify CYAM charges later.
   * **Credit limit (optional):** You may set a daily spending cap (e.g., `$1`). This only applies if you later add credits for paid models.
   * **Expiration (optional):** You may set an expiry date for the key.
   * Click **Create**. Your API key (starting with `sk-...`) will be shown **once only**. CYAM will securely capture and store it — you do not need to copy it manually.
5. **(Optional — for Frontier Models):** If you want access to premium AI models (Claude, GPT-4, Gemini Pro), you need to add prepaid credits:
   * Go to [openrouter.ai/settings](https://openrouter.ai/settings) and click **"Buy Credits"**.
   * Minimum top-up is **$5**. OpenRouter accepts credit/debit cards, Google Pay, Amazon Pay, Cash App, and USDC crypto.
   * **No subscriptions** — it's strictly pay-as-you-go. Credits last 365 days. Purchasing at least $10 in credits increases your rate limit from 50 to **1,000 requests/day**.
   * Your single API key works for both free and paid models. OpenRouter deducts the per-token cost from your credit balance automatically.

##### Level 5: Help & Context
* **Carousel Item 1:** Screenshot of the OpenRouter home page showing the "Get API Key" button.
  (Media: `openrouter_home.png`)
* **Carousel Item 2:** Screenshot of the "Create API Key" dialog showing the Name, Credit Limit, and Expiration fields.
  (Media: `openrouter_create_key.png`)
* **Carousel Item 3:** Screenshot of the "Your new key" confirmation dialog emphasizing "You will not be able to see it again."
  (Media: `openrouter_key_created.png`)
* **Chatbot Note:** Assist with OpenRouter API key naming and payment methods. Note that if authorization fails, it might be due to pop-up blockers, not being logged into OpenRouter, or an expired session.

---

### Level 3: Task 2 — Review & Customise AI Model Routing Table

#### Level 4: Steps

1. Return your attention to the CYAM Admin Console. You will see the **AI Model Routing Table** — a pre-configured table mapping every CYAM platform function to the best-suited AI model.
   * This table ships with sensible **CYAM Defaults** so you do not need AI expertise. Advanced users can change any model via the dropdowns.
   * The table is sourced from a central CSV file (`AI Model Routing Table.csv`) that can be updated by CYAM Marketplace or locally by the Admin.

2. **Understanding the Table Columns:**

   | Column | Purpose |
   |---|---|
   | **Function / Component** | The specific CYAM feature (e.g., Main Chat, Summarizer, Help & Context Chatbot). |
   | **Primary Model** | The first-choice model used for this function. May be free or paid. |
   | **Fallback / Escalation Model** | A backup model used when the primary fails **or** when an escalation trigger fires. |
   | **Escalation Trigger** | The condition that causes the system to switch from Primary to Fallback. |

3. **Review the pre-configured defaults.** CYAM ships the following routing for key functions:

   | Function | Primary Model | Fallback / Escalation | Trigger |
   |---|---|---|---|
   | Main Chat | `anthropic/claude-sonnet-4.6` | `openai/gpt-5.4` | Standard failover |
   | Help & Context Chatbot | `qwen/qwen-3.5-7b-instruct:free` | `x-ai/grok-4.1-fast` | `ESCALATE_TO_WEB` |
   | Council: Security | `anthropic/claude-opus-4.6` | `openai/gpt-5.4` | Standard failover |
   | Summarizer | `anthropic/claude-sonnet-4.6` | `openai/gpt-5.4` | Standard failover |
   | X / Grok Search | `x-ai/grok-4.1-fast` | — | Unique capability |
   | Deep Research | `google/gemini-deep-research-pro` | — | Unique capability |
   | Embeddings | `nomic/nomic-embed-text-v1.5` | — | Unique capability |

   *(This is a summary excerpt. The full table containing all 21 functions is visible in the Admin Console and in the CSV file.)*

4. **The Escalation Pattern (Help & Context Chatbot):**
   * The Help & Context Chatbot reads local `Context_Knowledge.md` documents (1–4 pages) to answer user questions using the **free** `qwen/qwen-3.5-7b-instruct` model — costing nothing.
   * If the answer is **not found** in the local documents, the model replies with a system trigger phrase: `ESCALATE_TO_WEB`.
   * CYAM automatically intercepts this trigger and re-routes the **same question** to `x-ai/grok-4.1-fast` — a model purpose-built for real-time web and social media search — to fetch a live answer.
   * **Result:** Users get accurate answers from local docs for free, and only consume paid credits when live web search is genuinely needed.

5. **Customise any model (optional):** Click on any **Primary Model** or **Fallback Model** dropdown in the table to change it. The dropdown is populated live from your connected OpenRouter account, showing available models and their per-token pricing. [Browse all models at openrouter.ai](https://openrouter.ai/).

6. **Configure Offloading for Simple Tasks:** To save your paid credits, simple background tasks can be offloaded from your premium models.
   * **Option A (Local Offloading):** If you successfully installed Ollama, toggle the switch labeled **"Enable Local Offloading"** to **ON**. This routes simple prompts to your computer using zero cloud credits.
   * **Option B (Free Cloud Offloading):** If your computer couldn't run Ollama, select from the **"Offloading Engine"** dropdown and choose a free model tagged with *$0* (e.g., `google/gemma-3-8b-it:free` or `openrouter/free`). This routes simple prompts securely to free cloud servers instead.

7. Click **"Save Configuration"**.

8. The CYAM WebApp will automatically execute a **Test Connection protocol** — sending a small test prompt (`"Say this is a test"`) securely from your web browser directly to OpenRouter to confirm routing is live.
   * **Marketplace Tier 1 Security (CASA) Compliance:** By running this test directly in your browser (client-side `fetch`), CYAM avoids requesting invasive server-side external network permissions (`script.external_request`) from your Google Workspace, maintaining the strictest security posture.

9. Wait for the test to complete.
   * ✅ **Success:** HTTP 200 response → green **"Verified & Active"** badge appears next to the workflow.
   * ❌ **Failure:** The exact HTTP error code is surfaced. Common errors:
       * 401 Unauthorized — API key is invalid or was revoked.
       * 402 Payment Required — Insufficient credits; add funds at [openrouter.ai/settings](https://openrouter.ai/settings).
       * 404 Not Found — Selected model ID no longer exists; choose a different model.
       * 429 Too Many Requests — Rate limit exceeded; wait and retry.
   * **Key Security Reminder:** Your OpenRouter API key is stored encrypted on the CYAM backend and is never exposed in browser requests or logs. If you believe a key is compromised, delete it immediately from [openrouter.ai/settings/keys](https://openrouter.ai/settings/keys) and re-run the OAuth flow.

##### Level 5: Help & Context
* **Carousel Item 1:** The AI Model Routing Table in the Admin Console, showing each CYAM function mapped to its Primary and Fallback models.
  (Media: `step10_routing_table.png`)
* **Carousel Item 2:** The Escalation Pattern: How the Help & Context Chatbot checks local documents first (free) and only escalates to a paid web-search model when the answer is missing.
  (Media: `step10b_escalation_explainer.png`)
* **Carousel Item 3:** Test Connection: Once successfully configured, a green Verified & Active badge will appear next to the workflow.
  (Media: `step13_test_connection_badge.png`)
* **Chatbot Note:** Assist with understanding the routing table, the escalation trigger pattern, and how to customise individual model assignments.

---

## Context & Chatbot Delivery Summary

| Field | Value |
|---|---|
| `INSTALL_CHATBOT` | `true` |
| `chatbot_context_file` | `Admin_Console_AI_Engines_Context_Knowledge.md` |
| Context URLs | Listed in `metadata.json` |
