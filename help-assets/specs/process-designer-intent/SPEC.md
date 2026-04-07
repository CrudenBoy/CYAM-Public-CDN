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

**Step 2 — Visual Node Mapping:**<br><br>**Overview:** Generates a real-time topology map to verify your architecture visually.<br><br>**Read-Only Canvas:** This visual flowchart is precisely a **read-only mirror** of the routing rules you defined in Step 1. You cannot edit node contents or routing connections directly on the canvas.<br><br>**Interactive Position:** While you cannot change the underlying logic on the map, you can drag the nodes around to arrange them visually.<br><br>**Making Changes:** To add, remove, or edit nodes, or modify routing rules, you must close the canvas, update the specific Nodes under Step 1, and press Generate Visual Map again.

---

### Level 3: Task 2 — Unified Tool Assessment

#### Level 4: Steps
1. **Step 1 — Main Engine Selection**
2. **Step 2 — Third-Party Tools**
3. **Step 3 — Run Feasibility Matrix**

##### Level 5: Help & Context

**Step 1 — Main Engine Selection:**<br><br>**What:** The main engine is the "brain base" that holds the workflow together. Options include Google Apps Script, Opal, or Google AI Studio.<br><br>**Why:** Different engines have different strengths. For example, Google Apps Script is free and works perfectly with Google tools, while Opal is great for multi-step AI reasoning.<br><br>**How:** Click the dropdown box to view your options. If you aren't sure which one is best, select "Let the AI Interview Me", and a chatbot panel will help you decide.

**Step 2 — Third-Party Tools:**<br><br>**What:** These are the external platforms where the AI will fetch data from or send data to, such as Slack, HubSpot, or Gmail.<br><br>**Why:** The workflow needs specific connection protocols and security keys for every single tool it touches. Listing them early ensures the system can connect securely.<br><br>**How:** Review the provided list of tools and check the boxes for the ones you need. If your tool isn't listed, click "Add Custom Tool" at the bottom.

**Step 3 — Run Feasibility Matrix:**<br><br>**What:** The automated matrix checks if your selected Main Engine can natively integrate with your selected Third-Party Tools.<br><br>**Why:** Certain engines have blind spots. Identifying these incompatibilities early saves hours of debugging by proactively suggesting workarounds like Python worker scripts.<br><br>**How:** Click the "Run Automated Feasibility Check" button. The system will print an analysis of any potential roadblocks below the button.<br><br>* **Chatbot Note:** Unsure which framework fulfills your workflow requirements? Chat with the bot and invoke the `/RGDD` Google Developer Knowledge MCP to answer technical capability questions.
