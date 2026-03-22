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

1. **Step 1 — Download Ollama for Desktop**
   - Click the **"Download Ollama"** button in the AI Engines panel to open `https://ollama.com/download` in a new tab.
   - Choose the installer matching your computer's operating system (Windows or macOS).
   - 📖 *See Help & Context panel for detailed guidance*
2. **Step 2 — Run the Installer**
   - Locate the downloaded file (`OllamaSetup.exe` on Windows or `Ollama.zip` on macOS) and run it.
   - Follow the on-screen prompts to complete the installation. On macOS, drag the Ollama icon into your Applications folder.
   - 📖 *See Help & Context panel for detailed guidance*
3. **Step 3 — Launch the Ollama App**
   - Open Ollama from your Start menu (Windows) or Applications folder (macOS).
   - Verify that the Ollama icon appears in your system tray (Windows) or menu bar (macOS). This indicates the local AI server is active and ready to accept CYAM's requests.
   - 📖 *See Help & Context panel for detailed guidance*

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

**Automate with AntiGravity:**
If you have the AntiGravity Agent (or Claude Code) installed in your terminal, you can skip Tasks 1 and 2 entirely! The agent will automatically install Ollama, pull Llama 3.1, DeepSeek-R1, and Nomic Embeddings, and start the local server.

:::AGENT_PROMPT

/cyam-setup-local-ai

:::

---

### Level 3: Task 2 — Pull Local Models (via Ollama GUI)

#### Level 4: Steps

1. **Step 1 — Open the Ollama Terminal/Command Prompt**
   - **Windows:** Search for "cmd" or "PowerShell" in your Start menu and open it.
   - **macOS:** Open "Terminal" from your Applications > Utilities folder.
   - 📖 *See Help & Context panel for detailed guidance*
2. **Step 2 — Pull the Llama 3.1 8B Model**
   - Type `ollama run llama3.1` (or click the command in the Guidance panel to copy it).
   - Wait for the download and checksum verification to complete. This is the primary model for local reasoning.
   - 📖 *See Help & Context panel for detailed guidance*
3. **Step 3 — Pull the Nomic Embeddings Model**
   - Type `ollama pull nomic-embed-text`.
   - This tiny model allows CYAM to perform local document search and memory management without sending data to the cloud.
   - 📖 *See Help & Context panel for detailed guidance*
4. **Step 4 — Pull the Phi-3 Mini Model (Optional)**
   - Type `ollama pull phi3` to download a ultra-fast, lightweight fallback model.
   - Phi-3 is recommended for lower-powered laptops where Llama 3.1 may run slowly.
   - 📖 *See Help & Context panel for detailed guidance*
5. **Step 5 — List Downloaded Models**
   - Type `ollama list` to confirm all models are correctly installed on your local machine.
   - Ensure the `STATUS` column shows them as ready.
   - 📖 *See Help & Context panel for detailed guidance*
6. **Step 6 — Verify Connection in CYAM**
   - Return to the CYAM Dashboard and check the status indicator.
   - It should now display **"Ollama: Active ✓"** in green.
   - 📖 *See Help & Context panel for detailed guidance*

##### Level 5: Help & Context

**Steps 1-2 — Terminal Setup & Primary Model:** Open a terminal (PowerShell on Windows, Terminal on macOS) and pull the primary reasoning model with `ollama run llama3.1`. The Ollama App acts as the local model registry. Unlike cloud interfaces, physical AI models must be downloaded entirely to your hard drive. We strongly recommend starting with `llama3.1` (8B parameters) as it offers strong reasoning capabilities while remaining small enough (4-5 GB) to run alongside your primary IDEs and browsers.

**Step 3 — Embeddings Model:** The `nomic-embed-text` model is a lightweight embedding model that powers CYAM's local document search and memory management. It consumes minimal resources and enables privacy-preserving semantic search without sending any data to the cloud.

**Steps 4-6 — Optional Models & Verification:** Phi-3 is an ultra-fast fallback model for lower-powered machines. After pulling your models, run `ollama list` to verify they are installed correctly, then return to the CYAM Dashboard to confirm the **"Ollama: Active ✓"** status indicator turns green. **Use the '< >' arrows below to view the visual step-by-step guide for pulling models.**

*   **Carousel Item 1:** Task 2, Step 2: Inside the Ollama App, locate the model dropdown at the top of the chat interface.
    (Media: `step5_ollama_gui_dropdown.png`)
*   **Carousel Item 2:** Task 2, Step 4: Search for your desired CYAM-approved model and click the download arrow icon directly in the UI.
    (Media: `step6_ollama_download_model.png`)
*   **Carousel Item 3:** Task 2, Step 3: Model Naming — Ollama models use a name:tag format. If you enter a name without a tag, Ollama defaults to the recommended parameter count.
    (Media: `step6b_ollama_model_tags.png`)
*   **Chatbot Note:** Rely purely on visual instructions for downloading models within the new Ollama GUI. Guidance on how to change the default storage drive using the `OLLAMA_MODELS` environment variable can be provided.

---

## Level 2: Select LLMs for Workflow Tasks
**Goal:** Link cloud billing and map specific models (Local or Cloud) to distinct CYAM platform functions.

### Level 3: Task 3 — Connect OpenRouter (Cloud BYOK)

#### Level 4: Steps

1. **Step 1 — Initiate Authorization**
   - Click the **"Authorize OpenRouter"** button in the AI Engines panel.
   - A secure **OpenRouter** authentication page will open in a new browser tab.
   - 💡 **Tip:** For the best experience, use Chrome's **Split-Screen** to place CYAM on the left and OpenRouter on the right — see the Help Carousel for a visual guide.
   - 📖 *See Help & Context panel for detailed guidance*
2. **Step 2 — Sign In or Create an Account**
   - In the **OpenRouter** tab that just opened, **sign in to your existing OpenRouter account**, or click **"Create Account"** to register for free.
   - This step is done entirely inside **OpenRouter** — not inside the CYAM Dashboard.
   - 📖 *See Help & Context panel for detailed guidance*
3. **Step 3 — Grant Access to CYAM**
   - Still in **OpenRouter**, review the listed permissions on the authorization screen, then click **"Authorize App"** to confirm.
   - This securely binds your **OpenRouter** account to CYAM's backend.
   - 📖 *See Help & Context panel for detailed guidance*
4. **Step 4 — Authorization Successful (Cross-Tab)**
   - A new browser tab will display "✅ Authorization Successful!" confirming your OpenRouter account is connected.
   - Close this tab safely and return to your original CYAM Dashboard tab.
   - 📖 *See Help & Context panel for detailed guidance*
5. **Step 5 — Verify the Connection in CYAM**
   - Click the **"Verify Connection"** button right next to the Authorize button.
   - The UI will check the server and display a green **"OpenRouter: Connected ✓"** status badge.
   - 📖 *See Help & Context panel for detailed guidance*
6. **Step 6 — Choose Your Access Path** *(Select one option below)*
   - Your choice determines which AI models will be available to CYAM.
   - Use the action cards below to select your path.
   - 📖 *See Help & Context panel for detailed guidance*


   **Path A — Free Tier:** No payment required. Use community and open-source models immediately.

   **Path B — Premium Credits:** Add prepaid credits ($5+) to unlock frontier models like GPT-4o, Claude 3.5.

   **Path C — BYOK:** Use your own provider API keys at direct rates with zero markup.

##### Level 5: Help & Context

**Steps 1-4 — Secure OAuth Authorization:**

- **Why no API key field?** CYAM uses OpenRouter's **PKCE OAuth 2.0 flow** — no API key is ever visible in your browser.
- When you click "Authorize", you log in securely on OpenRouter's own site.
- OpenRouter issues a short-lived authorization code; CYAM's backend exchanges it for a scoped token in a **server-to-server call**.
- **At no point does CYAM's frontend see, store, or transmit your API key.**
- The token can be revoked from OpenRouter's dashboard at any time.

💡 **Chrome Split-Screen Tip:**

- Right-click a tab → choose **"New split view with current tab"** (or drag a tab to the screen edge).
- Place CYAM Dashboard on the **left** and OpenRouter on the **right**.
- After clicking "Authorize" in Step 1, follow Steps 2-4 in the OpenRouter UI on the right side.
- Use the **'< >' carousel arrows** below for a visual step-by-step guide.

**Step 6 — Choose Your Access Path:**

This determines your funding mechanism and controls which models appear in Task 4's Routing Table.

- **Path A (Free Tier):**
  - No payment needed — immediate access to community models.
  - Ideal for development, testing, and proof-of-concept.
  - Rate limit: 50 requests/day (1,000/day after purchasing $10+ in credits).

- **Path B (Premium Credits):**
  - Buy prepaid credits at [openrouter.ai/settings/credits](https://openrouter.ai/settings/credits) — minimum $5.
  - Unlocks frontier models: GPT-4o, Claude 3.5 Sonnet, Gemini Pro.
  - Model prices match provider rates. A **5.5% fee** is applied when purchasing credits (not per-token).
  - Credits expire after 365 days. Pay-as-you-go, no subscription.

- **Path C (BYOK — Bring Your Own Key):**
  - Configure your own API keys at [openrouter.ai/workspaces/default/byok](https://openrouter.ai/workspaces/default/byok).
  - Same premium models as Path B, billed directly by each provider.
  - 1 million free BYOK requests/month; 5% fee on requests beyond that threshold.
  - Supported providers: OpenAI, Anthropic, Google, Mistral, Cohere.

- **You can switch paths at any time** — Task 4's routing table automatically reflects your available models.

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

1. **Step 1 — Open the Model Routing Table**
   - In the interactive panel **below these steps**, click the **"Open Routing Table"** button.
   - The routing table loads, displaying every **AI Task Type** that CYAM uses.
   - ⚠️ If the model dropdowns appear empty, return to **Task 3** and complete the OpenRouter connection first.
   - 📖 *See Help & Context panel for detailed guidance*
2. **Step 2 — Review AI Task Types**
   - Each row in the Routing Table represents a **Type of AI work** — not an individual feature. CYAM maps all its AI tools to these Types automatically.
   - The pre-filled models are **curated defaults** — each AI tool in the platform is designed around its assigned model. We recommend keeping the defaults unless you have specific needs.
   - 📖 *See Help & Context panel for detailed guidance*
3. **Step 3 — Change a Primary Cloud Model (Optional)**
   - **In the Routing Table below**, click the **Primary Model dropdown** for any row you wish to change, and select a different model from the list.
   - This is **optional** — the defaults are chosen for optimal performance.
   - 📖 *See Help & Context panel for detailed guidance*
4. **Step 4 — Assign a Fallback Model (Recommended)**
   - **In the Routing Table below**, click the **Fallback Model dropdown** for each critical AI Task Type and select a backup model.
   - If the primary model fails or hits rate limits, CYAM automatically switches to the fallback — with zero disruption.
   - 📖 *See Help & Context panel for detailed guidance*
5. **Step 5 — Enable Local Offloading via Ollama (Conditional)**
   - **In the Routing Table below**, flip the **Local Offloading toggle to ON** for any AI Task Type you want to run on your own machine.
   - When enabled, that row's Primary Model dropdown updates to show your locally available Ollama models instead of cloud options.
   - This toggle is disabled if Ollama is not detected on your machine.
   - 📖 *See Help & Context panel for detailed guidance*
6. **Step 6 — Save Your Configuration**
   - Click the **"Save Configuration"** button at the bottom of the **Routing Table below**.
   - CYAM validates the assignments, locks in your routing rules, and confirms the save with a green success banner.
   - 📖 *See Help & Context panel for detailed guidance*

##### Level 5: Help & Context

**Steps 1-2 — Understanding the Routing Table:**

- The Routing Table is a **dispatch board** — it maps each **AI Task Type** to the best model for that kind of work.
- Different AI tasks have **radically different requirements** — running everything through one model wastes credits and produces poor results:
  - Lightweight, fast model → quick summarization tasks
  - Capable frontier model → complex chat interactions
  - Embedding model → document search and memory
- Your credit spend is directed **precisely where it produces the most value**.
- The defaults are **curated** — each AI tool in CYAM is specifically designed around its assigned model. We recommend keeping them unless you have a specific reason to change.

**Automate with AntiGravity:**
If you have the AntiGravity Agent (or Claude Code) installed in your terminal, it can automatically fix connection issues and sync your local models to the routing table:

:::AGENT_PROMPT

/cyam-fix-ollama-bridge

:::

:::AGENT_PROMPT

/cyam-sync-local-models

:::
- **If the model dropdowns are empty**, return to Task 3 and complete the OpenRouter connection first.
- Click the **"Open Routing Table"** button in the interactive panel below to see every AI Task Type.

**Steps 3-4 — Primary & Fallback Model Strategy:**

- Changing a Primary Model is **optional** — the defaults are chosen for optimal performance.
- Provider outages and rate-limit exhaustion are **real operational risks**.
- When you assign a **Fallback Model**, CYAM implements automatic failover:
  - Primary model returns an error → engine immediately retries with the fallback.
  - **No user-visible disruption** — the switch is seamless.
- The **Help Chatbot** uses a special fallback pattern:
  - First attempts to answer via free local documentation.
  - Only triggers `ESCALATE_TO_WEB` when local docs don't have the answer.
  - This escalation uses a paid web-search model (e.g., Grok) only when necessary.

**Step 5 — Local Offloading with Ollama:**

- When enabled for an AI Task Type, CYAM **stops routing through OpenRouter entirely**.
- Requests go to the **Ollama runtime on your local machine** — zero API traffic.
- **Recommended for:** High-frequency, lower-stakes tasks (e.g., Embeddings).
- **Keep cloud models for:** Main Chat, complex reasoning, and web-search tasks.
- The toggle is **disabled** if Ollama is not detected running on your machine.
- Use the **'< >' carousel arrows** below for the visual routing configuration guide.

**Step 6 — BYOK in the Routing Table:**

- If you configured BYOK in Task 3, your Routing Table **works exactly the same**.
- You still select models using standard names like `openai/gpt-4o`.
- OpenRouter **automatically routes** matching requests through your personal key.
- **BYOK takes priority over credits** — your prepaid balance is preserved for non-BYOK providers.
- Compatible providers: OpenAI, Anthropic, Google, Mistral, Cohere.

**Step 7 — BYOK Cost Tracking:**

- BYOK requests are billed **directly by the provider** — they may not appear in OpenRouter's dashboard.
- Track BYOK costs at each provider:
  - **OpenAI:** `platform.openai.com/usage`
  - **Anthropic:** `console.anthropic.com/settings/usage`
  - **Google:** Google Cloud Console
- If a BYOK model suddenly fails, the issue is typically with the **provider** (expired payment, rate limits, key expiration) — resolve it through their dashboard, not CYAM's.
- Ask the **Help Chatbot** for BYOK troubleshooting assistance.

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
