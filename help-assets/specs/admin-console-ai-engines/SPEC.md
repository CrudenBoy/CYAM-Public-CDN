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

1. **Ollama Deployment Scope:** Ollama is a completely standalone local binary and daemon. You do not need the CYAM Web App, `gemini-cli`, or `clasp` installed to run it. However, installing it makes it permanently available to the CYAM environment.
2. **Select OS & Check Requirements:** The UI displays a direct download button for the official Ollama installer. Before downloading, confirm your machine meets minimum requirements:
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

**Step 1 — Ollama Deployment Scope:** AI models run as background daemons natively on your hardware. Unlike cloud deployments, you do not need the CYAM Web App, the AntiGravity Agent, or development packages like `gemini-cli` installed to operate Ollama. Once installed, it is permanently available to CYAM or any other local software silently in the background.

**Step 2 — System Requirements:** AI models are highly resource-intensive. Running a local LLM ensures data privacy and zero cloud cost, but it requires capable hardware. Verify you have at least Windows 10 22H2+ or macOS 14 Sonoma+, and a minimum of 4 GB free disk space just for the Ollama binary. Depending on the models you pull later, you may need an additional 10-100 GB of storage.

**Step 3 — Installation Execution:** Operating systems enforce strict security protocols against unrecognized binaries. On Windows, Windows SmartScreen will flag the unsigned `.exe` (Click 'More info' -> 'Run anyway'). On macOS, Gatekeeper will issue a warning, and installing the necessary CLI companion tool will demand your Mac Password or Touch ID. **Use the operating system buttons below and the '< >' arrows to view the visual step-by-step installation guide.**

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
6. **Cloud routing setup is next.** Once your local model finishes downloading, scroll down to Task 3 to connect your cloud fallback models.

##### Level 5: Help & Context

**Steps 1-2 — Open Ollama & Find Model:** The Ollama App acts as the local model registry. Unlike cloud interfaces, physical AI models must be downloaded entirely to your hard drive. By launching the app and interacting with the top model dropdown, you initiate a direct connection to the global Ollama library registry.

**Step 3 — Model Selection (qwen3:4b):** Selecting the right model size is essential to avoid system crashes. We strongly recommend `qwen3:4b` as it offers a 128K context window with high reasoning capabilities while remaining small enough (3-4 GB RAM) to run alongside your primary IDEs and web browsers transparently. Specifying the exact tag (e.g. `gemma3:4b`) ensures you do not accidentally pull an oversized 70B model that will choke your machine.

**Steps 4-5 — Download & Wait:** The downloading process creates the model binary shards on your disk. You must wait for this 2.6 GB transfer to complete fully; interrupting it forces Ollama to resume from its last completed digest layer. **Use the '< >' arrows below to view the visual step-by-step guide for pulling models via the GUI.**

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

### Level 3: Task 3 — Connect OpenRouter (Cloud BYOK)

#### Level 4: Steps

1. **Step 3.1 — Initiate Authorization**
   Click the **"Authorize OpenRouter"** button in the AI Engines panel. A secure **OpenRouter** authentication page will open in a new browser tab. **💡 Optional (Recommended):** Before clicking, set up **Chrome Split-Screen** so you can see the CYAM Dashboard on the left and **OpenRouter** on the right — right-click a tab and choose "New split view" or drag a tab to the screen edge. See the Help & Context panel for a visual guide.
2. **Step 3.2 — Sign In or Create an Account**
   In the **OpenRouter** tab that just opened, **sign in to your existing OpenRouter account**, or click **"Create Account"** to register for free. This step is done entirely inside **OpenRouter** — not inside the CYAM Dashboard. A free account provides immediate access to zero-cost models.
3. **Step 3.3 — Grant Access to CYAM**
   Still in **OpenRouter**, review the listed permissions on the authorization screen, then click **"Authorize App"** to confirm. This securely binds your **OpenRouter** account to CYAM's backend.
4. **Step 3.4 — Confirm the Connection in CYAM**
   You will be redirected back to the CYAM Dashboard. Verify that the **"OpenRouter: Connected ✓"** status indicator is green in the AI Engines panel. If it remains pending, click **"Re-check Connection"** to trigger a manual handshake.
5. **Step 3.5 — Choose Your Access Path** *(Select one option below)*
   Your choice here determines which AI models will be available to CYAM:

   **Path A — Free Tier (No Payment Required):**
   - Verify the "Connected to OpenRouter" status from Steps 3.1-3.4. No payment configuration is required — OpenRouter provides immediate access to community and open-source models.
   - Available free models include: `meta-llama/llama-3.1-8b-instruct:free`, `google/gemma-2-9b-it:free`, `mistralai/mistral-7b-instruct:free` (availability may vary).
   - Free-tier accounts remain valid indefinitely. Click **"Continue with Free Models"** to proceed to Task 4.

   **Path B — Premium Models via Credits:**
   - Click the **"Open Credits Settings ↗"** button to open `https://openrouter.ai/settings/credits` in a new tab.
   - Click **"Add Credits"** and deposit a minimum of **$5.00 USD**. Credits are prepaid and consumed per-token with a 10-20% OpenRouter markup over base provider pricing.
   - Adding credits unlocks frontier models: `openai/gpt-4o`, `anthropic/claude-3.5-sonnet`, `google/gemini-pro-1.5`. Return to CYAM — premium models are immediately available in Task 4.

   **Path C — Bring Your Own Key (BYOK):**
   - Click the **"Open BYOK Settings ↗"** button to open `https://openrouter.ai/workspaces/default/byok` in a new tab.
   - Add your API keys from providers: **OpenAI** (`platform.openai.com/api-keys`), **Anthropic** (`console.anthropic.com/settings/keys`), or others listed on the BYOK page.
   - **⚠️ CRITICAL:** Configure keys in OpenRouter's BYOK page ONLY. Do NOT paste provider API keys into the CYAM Dashboard. CYAM communicates exclusively with OpenRouter.
   - If using multiple providers (e.g., both OpenAI AND Anthropic), each key must be added separately in OpenRouter's BYOK settings.
   - BYOK routes requests through your personal keys at direct provider rates with **zero OpenRouter markup**. Return to CYAM — provider models are available in Task 4.

##### Level 5: Help & Context

**Steps 3.1–3.4 — Secure OAuth Authorization:** You may have noticed that CYAM never asks you to paste an API key directly into any field in the dashboard. This is intentional. CYAM uses OpenRouter's **PKCE OAuth 2.0 flow** which means no API key is ever visible in your browser. When you click "Authorize", you log in securely on OpenRouter's own site. OpenRouter issues a short-lived authorization code and CYAM's backend exchanges it for a scoped token in a server-to-server call. **At no point does CYAM's frontend see, store, or transmit your API key.** The token can be revoked from OpenRouter's dashboard at any time. **💡 Tip:** For the best experience, use **Chrome's Split-Screen** to place the CYAM Dashboard on the left and OpenRouter on the right — right-click a tab and choose "New split view" or drag a tab to the edge. After clicking "Authorize" in Step 3.1, follow Steps 3.2 to 3.4 in the OpenRouter UI on the right side. **Use the '< >' arrows below to view the visual step-by-step guide, and ask the Help Chatbot below for personalized assistance at any time.**

**Step 3.5 — Choose Your Access Path:** This step determines your funding mechanism and directly controls which AI models become available in Task 4's routing table. **Path A (Free Tier)** provides immediate access to community models without payment setup — ideal for development, testing, and proof-of-concept work. **Path B (Credits)** unlocks frontier models like GPT-4o and Claude 3.5 Sonnet through OpenRouter's unified prepaid system with a 10-20% markup. **Path C (BYOK)** offers the same premium models at direct provider rates with zero markup by using your own API keys configured inside OpenRouter. You can change paths at any time by returning to this step — your Task 4 routing table will automatically reflect the models available under your current access configuration. If uncertain, start with Path A to validate your CYAM integration, then upgrade when ready for production.

* **Carousel Item 1:** Part 1 — Open Chrome's menu → More Tools → Customize Chrome to access toolbar settings.
  (Media: `step3_chrome_split_01.png`)
* **Carousel Item 2:** Part 1 — Inside Customize Chrome, click the **Toolbar** section to manage toolbar buttons.
  (Media: `step3_chrome_split_02.png`)
* **Carousel Item 3:** Part 1 — Turn on the **Open In Split View** toggle to enable Split View in the toolbar.
  (Media: `step3_chrome_split_03.png`)
* **Carousel Item 4:** Part 2 — Open the CYAM Dashboard in one tab and OpenRouter (`openrouter.ai/settings/keys`) in a second tab.
  (Media: `step3_chrome_split_04.png`)
* **Carousel Item 5:** Part 2 — Right-click the OpenRouter tab and choose **"New split view with current tab"** to start Split View.
  (Media: `step3_chrome_split_05.png`)
* **Carousel Item 6:** Part 2 — Place CYAM Dashboard on the **left** and OpenRouter on the **right**. Swap if needed.
  (Media: `step3_chrome_split_06.png`)
* **Carousel Item 7:** Part 2 — Drag the center divider to resize. Exit Split View by separating views back into regular tabs.
  (Media: `step3_chrome_split_07.png`)
* **Chatbot Note:** Assist with OpenRouter OAuth connection concepts, Chrome Split-Screen setup, and the BYOK funding paths.

---

### Level 3: Task 4 — Configure CYAM Routing & Offloading

#### Level 4: Steps

1. **Step 4.1 — Open the Model Routing Table**
   Click the **"Model Routing"** tab in the AI Engines panel. The routing table loads, displaying every CYAM function that requires an AI model assignment.
2. **Step 4.2 — Review All Function Rows**
   Scan each row in the table (e.g., **Main Chat**, **Summarizer**, **Code Assistant**). Confirm that the pre-filled default model shown in the **"Primary Model"** column is appropriate for your deployment.
3. **Step 4.3 — Reassign a Primary Cloud Model (if needed)**
   For any function whose default model you want to change, click the **dropdown in the "Primary Model" column** of that row and select a different OpenRouter model from the list.
4. **Step 4.4 — Assign a Fallback Model (Recommended)**
   For each critical function, click the **dropdown in the "Fallback Model" column** and select a backup model. This model activates automatically if the primary is unavailable.
5. **Step 4.5 — Enable Local Offloading via Ollama (Conditional)**
   For any function you want to run locally, flip the **"Local Offloading" toggle to ON** in that function's row. The row's Primary Model dropdown will update to display your locally available Ollama models instead of cloud options.
6. **Step 4.6 — Save Your Configuration**
   Click **"Save Configuration"** at the bottom of the routing table. CYAM validates the assignments, locks in your routing rules, and automatically verifies the connection.

##### Level 5: Help & Context

**Steps 1-2 — Routing Table Overview:** Different AI tasks have radically different requirements. Running every single CYAM function through the same single model would be wasteful at best and produce noticeably poor results at worst. The Model Routing Table solves this by letting you assign the right model to the right job. Think of it as a dispatch board: you can run a lightweight, fast model for quick summarization while reserving a more capable frontier model exclusively for complex chat interactions. Your credit spend is directed precisely where it produces the most value. Open the Model Routing tab in the interactive panel below to see every CYAM function that requires an AI model assignment.

**Steps 3-4 — Fallback Model Strategy:** Provider outages and rate-limit exhaustion are real operational risks. When you assign a Fallback Model to a function row, CYAM implements automatic failover. If a call to the primary model returns an error, the engine immediately retries the identical request against the fallback model with no user-visible disruption. The CYAM Help Chatbot heavily relies on fallbacks, aggressively attempting to answer questions via free local documentation first, and only triggering an `ESCALATE_TO_WEB` state when it natively decides to fallback to an expensive live web-search model.

**Step 5 — Local Offloading with Ollama:** When the Local Offloading toggle is enabled for a function, CYAM stops routing that function's AI calls through OpenRouter completely. Instead, it sends those requests to the Ollama runtime running on your local machine, consuming zero external API traffic. Enable Local Offloading for high-frequency, lower-stakes functions (like Embeddings) while keeping cloud models assigned to Main Chat. **Use the '< >' arrows below to view the visual step-by-step routing configuration guide.**

**Step 6 — Understanding BYOK in the Routing Table:** If you configured a Bring Your Own Key (BYOK) in Task 3 Step 5, your Routing Table works exactly the same — you still select models using standard names like `openai/gpt-4o`. OpenRouter automatically routes matching requests through your personal key at direct provider pricing with zero markup. BYOK takes priority over credits automatically, so your OpenRouter credits are preserved for providers where you haven't configured BYOK. BYOK-compatible providers include OpenAI, Anthropic, Google, Mistral, and Cohere. Look for the 🔑 icon next to model providers in the dropdowns.

**Step 7 — BYOK Cost Tracking:** BYOK requests are billed directly by the provider and may not appear in OpenRouter's usage dashboard. To track BYOK costs, check your provider dashboards directly: OpenAI at `platform.openai.com/usage`, Anthropic at `console.anthropic.com/settings/usage`, or Google in the Cloud Console. If a BYOK model suddenly stops working, the issue typically originates with the provider (expired payment, rate limits, key expiration) — resolve it through their dashboard, not CYAM's. **Ask the Help Chatbot for more details on BYOK troubleshooting.**

* **Carousel Item 1:** The AI Model Routing Table in the Admin Console, showing each CYAM function mapped to its Primary and Fallback models.
  (Media: `step10_routing_table.png`)
* **Carousel Item 2:** The Escalation Pattern: How the Help & Context Chatbot checks local documents first (free) and only escalates to a paid web-search model when the answer is missing.
  (Media: `step10b_escalation_explainer.png`)
* **Carousel Item 3:** Test Connection: Once successfully configured, a green Verified & Active badge will appear next to the workflow.
  (Media: `step13_test_connection_badge.png`)
* **Chatbot Note:** Assist with understanding the routing table dispatch logic, the escalation trigger pattern, and Ollama vs Cloud model trade-offs.

---

## Context & Chatbot Delivery Summary

| Field | Value |
|---|---|
| `INSTALL_CHATBOT` | `true` |
| `chatbot_context_file` | `Admin_Console_AI_Engines_Context_Knowledge.md` |
| Context URLs | Listed in `metadata.json` |
