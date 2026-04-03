---
spec_id: "process-designer-intent"
spec_version: "1.0"
generated_by: "CYAM_Spec_Designer"
generated_date: "2026-04-03"
category: "Agent & Workflow Designer"
---

# Specification: Process Designer — Intent Mapping & Tool Assessment

## Level 1: Category
* **Category:** Agent & Workflow Designer
* **Permissions:** Restricted to `User_Signups.Role=Admin` (WDE actors).

---

> **📋 Purpose**
> This Workflow establishes the process intent by extracting human domain expertise and collaboratively selecting the optimal execution engine.

---

## Level 2: Intent Mapping & Tool Assessment
**Goal:** Map out Brain vs Hands nodes, and decide on the target execution engine and third-party tools.

### Level 3: Task 1 — pd_task_node_mapping

#### Level 4: Steps
1. **Step 1 — Identify Brain Steps (Thinking)**
2. **Step 2 — Identify Hands Steps (Doing)**
3. **Step 3 — Attach Training Documents**

##### Level 5: Help & Context

**Step Guidance — Operating Modes (A vs B):**
• **What: Mode A (Auto) vs. Mode B (Cyborg)**
• **Mode A (Auto):** The AI operates completely autonomously, making decisions without any human intervention. You trust the logic completely.
• **Mode B (Cyborg):** The AI pauses at critical decision gates and requests explicit human approval before proceeding. Useful for high-risk or subjective actions.
• **How:** Toggle the Operating Mode at the top right of the page to focus your brain/hands node mapping on the chosen operational style. 

**Step 1 — Identify Brain Steps (Thinking):**
• **What:** Brain steps are tasks that require human-like judgment, such as reading an email to understand the sender's tone or comparing a lead against a complex rubric.
• **Why:** The AI needs explicit instructions on exactly what subjective decisions it is responsible for. If it doesn't know it's supposed to evaluate something, it will just follow blindly.
• **How:** Write down each decision clearly. For example, "1. Read the incoming email and determine if the customer is angry or happy."

**Step 2 — Identify Hands Steps (Doing):**
• **What:** Hands steps are mechanical actions like fetching data from a database, searching the web, or sending an email.
• **Why:** The system must map out every third-party integration required. This ensures the workflow is granted the correct security permissions and API keys.
• **How:** List out the mechanical steps in order. For example, "1. Fetch the CRM record from HubSpot. 2. Draft an email in Gmail. 3. Create a Jira ticket."

**Step 3 — Attach Training Documents:**
• **What:** This is where you upload grading rubrics, brand guidelines, or standard operating procedures.
• **Why:** The AI uses these documents as the undisputed source of truth to execute the "Brain" steps you defined earlier without making mistakes.
• **How:** Click 'Attach Reference Document' and select a Google Doc, Spreadsheet, or PDF that contains the specific rules for the AI to follow.

* **Chatbot Note:** Need help determining if a node is "Brain" or "Hands"? Ask the Chatbot to analyze your raw SOP!

---

### Level 3: Task 2 — pd_task_tool_assessment

#### Level 4: Steps
1. **Step 1 — Main Engine Selection**
2. **Step 2 — Third-Party Tools**
3. **Step 3 — Run Feasibility Matrix**

##### Level 5: Help & Context

**Step Guidance — Operating Modes (A vs B):**
• **What: How Modes affect Tool Selection**
• **Why:** If you select Mode B (Cyborg) in the previous step, your primary engine MUST support human-in-the-loop interactions (e.g. Slack approvals, Telegram Webhooks). Mode A workflows can run entirely in background cron jobs (e.g. Google Apps Script time-driven triggers).
• **How:** Keep your intended Operating Mode in mind when selecting your primary engine and secondary tools. Ensure you include a communication tool like Slack or Telegram if doing Cyborg validation.

**Step 1 — Main Engine Selection:**
• **What:** The main engine is the "brain base" that holds the workflow together. Options include Google Apps Script, Opal, or Google AI Studio.
• **Why:** Different engines have different strengths. For example, Google Apps Script is free and works perfectly with Google tools, while Opal is great for multi-step AI reasoning.
• **How:** Click the dropdown box to view your options. If you aren't sure which one is best, select "Let the AI Interview Me", and a chatbot panel will help you decide.

**Step 2 — Third-Party Tools:**
• **What:** These are the external platforms where the AI will fetch data from or send data to, such as Slack, HubSpot, or Gmail.
• **Why:** The workflow needs specific connection protocols and security keys for every single tool it touches. Listing them early ensures the system can connect securely.
• **How:** Review the provided list of tools and check the boxes for the ones you need. If your tool isn't listed, click "Add Custom Tool" at the bottom.

**Step 3 — Run Feasibility Matrix:**
• **What:** The automated matrix checks if your selected Main Engine can natively integrate with your selected Third-Party Tools.
• **Why:** Certain engines have blind spots. Identifying these incompatibilities early saves hours of debugging by proactively suggesting workarounds like Python worker scripts.
• **How:** Click the "Run Automated Feasibility Check" button. The system will print an analysis of any potential roadblocks below the button.

* **Chatbot Note:** Unsure which framework fulfills your workflow requirements? Chat with the bot and invoke the `/RGDD` Google Developer Knowledge MCP to answer technical capability questions.
