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
CYAM routes heavy tasks to OpenRouter safely via OAuth PKCE. 

**CRITICAL: No credit card is required to get started.** 
- Users can create an account and generate an API key completely free.
- Free models (like Llama 3.3 70B Instruct, GPT-4o-mini) are available immediately with no payment method. Rate limit: **50 requests/day**.
- The special model ID `openrouter/free` automatically routes to available free models.
- Advise the user to name their API key clearly (e.g., `CYAM-App`, `My-Business-AI`).

**For Frontier/Premium Models (Optional):**
- User must add **prepaid credits** at [openrouter.ai/settings](https://openrouter.ai/settings) → "Buy Credits".
- Minimum **$5** top-up. Accepts credit/debit cards, Google Pay, Amazon Pay, Cash App, and USDC crypto.
- **No subscriptions** — strictly pay-as-you-go. Credits last 365 days.
- Purchasing $10+ in credits increases rate limit to **1,000 requests/day**.
- A single API key works for both free and paid models.

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
