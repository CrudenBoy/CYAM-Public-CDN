# Help & Carousel Asset Specification

**CRITICAL ASSET RULES (For the Designer):**
1. **No Text Overlays**: Do NOT add any text overlays, floating captions, watermarks, or step numbers onto the image itself. The dashboard UI will dynamically add a sleek gradient caption over the bottom 100px of the image.
2. **Dimensions**: All screenshots MUST be strictly 1200 x 675 px (16:9 Aspect Ratio) to ensure uniformity in the UI carousel.
3. **Multiple Groups (carousel_group)**: N/A for these remaining tasks (No OS branching required here).

**IMPORTANT NOTE FOR EXTERNAL UIs**: The steps below involve external applications (Ollama GUI) and third-party dashboards (OpenRouter). You must generate or capture appropriately cropped screenshots (1200x675) for these specific steps so they can be added to the Help Carousel manually.

---

## 1. Global Media Metadata
* **Process ID**: `admin-console-ai-engines`
* **Asset Destination**: `CYAM-Public-CDN/help-assets/images/admin-console-ai-engines/`

## 2. Execution Environment & State Setup
* **State 1**: Desktop environment with the new Ollama GUI Chat App open.
* **State 2**: Browser logged into `openrouter.ai/settings/keys` with dark mode enabled.
* **State 3**: Browser logged into the CYAM Admin Console AI Routing page.
* **State 4**: Browser showing the CYAM Dashboard with the new FAB Chatbot open, Path cards visible, and accordion step blocks.

## 3. End-to-End Walkthrough Script (Video)
*(Video walkthrough generation is suspended for this specific generation request. Focus exclusively on the 9 Help Carousel static assets below).*

## 4. Help Carousel Step-by-Step Asset Mapping

### Task 2: Review & Customise AI Model Routing Table
#### Step 2: Open Model Dropdown
* **Source**: `[User-Provided Screenshot / AI Generation]`
* **Trigger Moment**: `Capture inside the Ollama desktop app, clearly showing the model selection dropdown menu at the top of the chat interface.`
* **Post-Processing Instruction**: `Must provide an appropriately cropped 1200x675 image. NO TEXT OVERLAYS.`
* **Target Filename**: `step5_ollama_gui_dropdown.png`

#### Step 3: Model Tag Concept
* **Source**: `[User-Provided Screenshot / AI Generation]`
* **Trigger Moment**: `Capture a close-up or stylized clean shot of the Ollama model search highlighting the concept of a model tag (e.g. "gemma3:4b").`
* **Post-Processing Instruction**: `Must provide an appropriately cropped 1200x675 image. NO TEXT OVERLAYS.`
* **Target Filename**: `step6b_ollama_model_tags.png`

#### Step 4: Download Model
* **Source**: `[User-Provided Screenshot / AI Generation]`
* **Trigger Moment**: `Capture the Ollama app search dropdown expanded, searching for "qwen3:4b" with a mouse hovering over the download (arrow) icon next to it.`
* **Post-Processing Instruction**: `Must provide an appropriately cropped 1200x675 image. NO TEXT OVERLAYS.`
* **Target Filename**: `step6_ollama_download_model.png`

### Task 3: Connect OpenRouter (Cloud BYOK)
#### Step 4a: OpenRouter Dashboard
* **Source**: `[User-Provided Screenshot / AI Generation]`
* **Trigger Moment**: `Capture the OpenRouter dashboard (openrouter.ai/settings/keys) showing the dark theme UI with the "Create Key" button visible.`
* **Post-Processing Instruction**: `Must provide an appropriately cropped 1200x675 image. NO TEXT OVERLAYS.`
* **Target Filename**: `openrouter_home.png`

#### Step 4b: Create Key Modal
* **Source**: `[User-Provided Screenshot / AI Generation]`
* **Trigger Moment**: `Capture the OpenRouter "Create Key" modal dialog, showing blank form fields for "Name", "Credit limit", and "Expiration".`
* **Post-Processing Instruction**: `Must provide an appropriately cropped 1200x675 image. NO TEXT OVERLAYS.`
* **Target Filename**: `openrouter_create_key.png`

#### Step 4c: Key Confirmation
* **Source**: `[User-Provided Screenshot / AI Generation]`
* **Trigger Moment**: `Capture the "Key Created" success modal, showing a blurred/asterisk API key string (sk-or-v1-***) and a warning message that the key will not be shown again.`
* **Post-Processing Instruction**: `Must provide an appropriately cropped 1200x675 image. NO TEXT OVERLAYS.`
* **Target Filename**: `openrouter_key_created.png`

#### Step 5: Choose Your Path (Action Cards)
* **Source**: `[User-Provided Screenshot / AI Generation]`
* **Trigger Moment**: `Capture the three Path cards (Free Tier, Premium Credits, BYOK) displayed in a grid with lucide icons and styled action buttons.`
* **Post-Processing Instruction**: `Must provide an appropriately cropped 1200x675 image. NO TEXT OVERLAYS.`
* **Target Filename**: `step5_path_cards.png`

### Task 4: Configure Cloud Routing
#### Step 1: Review Routing Table
* **Source**: `[User-Provided Screenshot / AI Generation]`
* **Trigger Moment**: `Capture a sleek web dashboard table titled "Model Routing" with columns for "Function", "Primary Model", "Fallback Model", and "Local". Show the "Open Routing Table" button clicked.`
* **Post-Processing Instruction**: `Must provide an appropriately cropped 1200x675 image. NO TEXT OVERLAYS.`
* **Target Filename**: `step10_routing_table.png`

#### Step 4: Escalation Explainer
* **Source**: `[User-Provided Screenshot / AI Generation]`
* **Trigger Moment**: `Capture a clean infographic-style UI flowchart showing: User Question -> Check Local Docs (Free) -> ESCALATE_TO_WEB trigger -> Live Web Search (Grok).`
* **Post-Processing Instruction**: `Must provide an appropriately cropped 1200x675 image. NO TEXT OVERLAYS.`
* **Target Filename**: `step10b_escalation_explainer.png`

#### Step 9: Test Connection Badge
* **Source**: `[User-Provided Screenshot / AI Generation]`
* **Trigger Moment**: `Capture a close-up UI shot of a successfully saved workflow configuration card in a dashboard, prominently featuring a green pill badge that says "Verified & Active".`
* **Post-Processing Instruction**: `Must provide an appropriately cropped 1200x675 image. NO TEXT OVERLAYS.`
* **Target Filename**: `step13_test_connection_badge.png`

### Dashboard UI Elements
#### FAB Chatbot & Step Blocks
* **Source**: `[User-Provided Screenshot / AI Generation]`
* **Trigger Moment**: `Capture the floating gradient Chatbot panel open on the bottom right (sparkles icon visible), with bulleted step blocks (accordion style) visible in the right side context panel.`
* **Post-Processing Instruction**: `Must provide an appropriately cropped 1200x675 image. NO TEXT OVERLAYS.`
* **Target Filename**: `dashboard_fab_chatbot.png`

---

## 5. Metadata Integration & CDN Rollout
*Instructions for finalizing and deploying the visuals.*

### Local Directory Cleanup
1. Ensure you are in the CDN repository: `cd ~/dev/CYAM-Platform/CYAM-Public-CDN`
2. Create the workflow folders:
   - `mkdir -p help-assets/images/admin-console-ai-engines`
   - `mkdir -p help-assets/videos/admin-console-ai-engines`
   - `mkdir -p help-assets/specs/admin-console-ai-engines`

### Asset Migration
1. Copy all 9 generated `.png` files into `help-assets/images/admin-console-ai-engines/`
2. *Wait for user upload of assets before committing...*
