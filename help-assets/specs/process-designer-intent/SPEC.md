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

### Level 3: Task 1 — Map the Process (Brain vs. Hands)

#### Level 4: Steps
1. **Step 1 — Review AI Extractions (Process Nodes)**
2. **Step 2 — Visual Node Mapping**

##### Level 5: Help & Context

**Step 1 — Review AI Extractions (Process Nodes):**<br><br>**Overview:** Step 1 and Step 2 work together to build your workflow blueprint. In Step 1, you design the logic and structure of every node. Then in Step 2, you generate a visual map to check your routing.<br><br>**Node Building Blocks:** The raw text steps extracted from Workflow 1. Add manual steps, delete unnecessary ones, or drag the ⠿ handle up and down to logically reorder the workflow sequence.<br><br>**Node Type:** Defines how the system executes a node. A **Decision** node requires the AI to evaluate logic (e.g., classify an email). An **Action** node runs mechanical APIs (e.g., save to Google Drive).<br><br>**AI Business Analyst:** This opens a chatbot that interrogates you to write a strict, machine-readable logic block (Technical Spec). You must generate a spec for every step to identify the exact data sources required.<br><br>**Intelligent Routing:** This tells the process where to go next. For **Decision** nodes, you set conditional branching (If TRUE / If FALSE). For **Action** nodes, you select the sequential next step or choose STOP to terminate the path.<br><br>**Reference Documents:** Click **Attach Document** to link a Google Doc or Spreadsheet. This acts as the undisputed source of truth and prevents hallucination during execution.

**Step 2 — Visual Node Mapping:**<br><br>**Overview:** Generates a real-time topology map to verify your architecture visually.<br><br>**Scratchpad Canvas:** ⚠️ **Warning: This Canvas is a Scratchpad.** You can freely drag nodes and draw connection lines to visually think through the process. However, **changes here will be lost when you close the map.**<br><br>**Recording Changes:** Take a screenshot of your visual arrangement for reference, then return to Step 1 to make the underlying modifications to your workflow specification.<br><br>**Making Changes:** To add, remove, or edit nodes, or modify routing rules, you must close the canvas, update the specific Nodes under Step 1, and press Generate Visual Map again.

---

### Level 3: Task 2 — Unified Tool Assessment

#### Level 4: Steps
1. **Step 1 — Platform Selection**
2. **Step 2 — Advanced Requirements**
3. **Step 3 — Third-Party Tools**
4. **Step 4 — Automated Feasibility Check**

##### Level 5: Help & Context

**Step 1 — Platform Selection:**<br><br>**What:** Instead of letting the AI guess where your workflow should run, you must select the Primary Platform (your first choice) and an Alternative Platform (Plan B).<br><br>**Why:** This is how you build an iron-clad "fence" around the AI. By explicitly constraining the architecture here, you physically prevent the AI from hallucinating impossible code during code generation. If the AI realizes your Primary choice has rigid timeout limits or lacks required functionality, it will scrap the design and route execution to the Alternative platform instead.<br><br>**How:** First, select your Primary Platform. Then, select a mandatory Backup. If you don't know which Workflow platform to choose, click the Help Bot at the bottom right. The bot will reference your User_Profile to seamlessly guide your decision.

**Step 2 — Advanced Requirements:**<br><br>**What:** Specific system capabilities your workflow relies on, such as creating files in Google Drive, caching context memory, utilizing visual nodes, or local agent execution.<br><br>**Why:** Identifying hard technical requirements early helps filter out incompatible platforms before writing any code.<br><br>**How:** Select the checkboxes that accurately reflect what your process specifically requires to function.

**Step 3 — Third-Party Tools:**<br><br>**What:** External platforms where the AI will fetch data from or send data to, such as Slack, HubSpot, or Gmail.<br><br>**Why:** The workflow needs specific connection protocols and security keys for every single tool it touches. Listing them early ensures the system can connect securely and guarantees your chosen platforms are technically capable of integrating with them.<br><br>**How:** Review the provided list of apps and check the boxes for the ones you need. If your tool isn't listed, click "Add Custom Tool" at the bottom.

**Step 4 — Automated Feasibility Check:**<br><br>**What:** The system runs a validation matrix to verify that the Primary and Alternative platforms can support your chosen constraints and tools.<br><br>**Why:** Certain platforms have intentional blind spots. Catching these early saves hours of debugging by warning you ahead of time.<br><br>**How:** Click "Run Automated Feasibility Check". Then, finalize the blueprint by saving your choices. The CYAM Platform's Admin Console contains detailed workflows (Google AntiGravity Installation Guide, Developer CLI Setup) to help you instantly install any missing dependencies later.


---

### Level 3: Task 3 — Intent Mapping & Discovery

#### Level 4: Steps
1. **Step 1 — Complexity Classification**
2. **Step 2 — Skill & Template Discovery**
3. **Step 3 — Validation Gate**

##### Level 5: Help & Context

**Step 1 — Complexity Classification:**<br><br>**Overview:** Analyze the selected process node and decide if it is straightforward or requires complex AI evaluation.

**Step 2 — Skill & Template Discovery:**<br><br>**Overview:** Search the SKILL.md registry and CYAM Templates to find validated logic that matches your intent.

**Step 3 — Validation Gate:**<br><br>**Overview:** Confirm compliance with CASA limits and execution timeouts before locking the skill to the node.