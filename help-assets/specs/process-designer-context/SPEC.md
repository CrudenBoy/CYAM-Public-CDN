---
spec_id: "process-designer-context"
spec_version: "1.0"
generated_by: "CYAM_Spec_Designer"
generated_date: "2026-04-02"
category: "Agent & Workflow Designer"
---

# Specification: Process Designer — Context & Knowledge Integration

## Level 1: Category
* **Category:** Agent & Workflow Designer
* **Permissions:** Restricted to `User_Signups.Role=Admin` (WDE actors).

---

> **📋 Purpose**
> This Workflow gathers information from the Workflow Domain Expert (WDE) to create a **portable Specification** — a structured document consumed by any downstream execution platform (Google AI Studio, Opal, GWS CLI, etc.). The CYAM Dashboard_v2 SPA is the *authoring interface*, not the execution target.

> **🎭 Stage: Stage 1 — Specification Design**
> Primary Actor: **Workflow Domain Expert (WDE)**. End Users do not interact with this Workflow. They receive the published Plugin in Stage 3.

---

## Level 2: Context & Knowledge Integration
**Goal:** Classify the workflow's complexity, gather foundational building blocks (goals, SOPs, context file requirements), and map them to the CYAM environment. Output: `WF1_CONTEXT_PAYLOAD`.

### Level 3: Task 1 — Goal, Output & Trigger Ingestion

#### Level 4: Steps

1. **Step 1 — Describe the Goal**
   - *"What is the primary goal of the process you are designing? Describe the current process being automated and provide concrete examples of desired output."*
   - Enter a detailed description in the text area below.
   - 📖 *See Help & Context panel for detailed guidance*
2. **Step 2 — Select Trigger Type**
   - Choose how this workflow will be initiated. Select one or more triggers from the chips below: **Webhook**, **Schedule**, **AppSheet Button**, **Manual**, **Other**.
   - 📖 *See Help & Context panel for detailed guidance*
3. **Step 3 — Upload Spec-Writing Material (Bucket A)**
   - Upload any files that will help the AI write the Specification in Workflow 3. Examples: existing SOPs, brand voice documents, draft process maps, reference materials.
   - Click **"Upload Material"** to open the Google Drive Picker.
   - These files feed the spec-writing AI — they do not go to the End User.
   - 📖 *See Help & Context panel for detailed guidance*
4. **Step 4 — Define End User Context Requirements (Bucket B)**
   - Specify what context files the End User must provide in Stage 3 when they adopt this workflow.
   - For each item, classify as:
     - **Definite** — The End User *must* provide this (e.g., "Brand Voice Markdown is required").
     - **Optional** — Recommended to optimise the prompt (e.g., "Colour palette file improves output quality").
   - Optionally upload template examples showing the expected file format.
   - 📖 *See Help & Context panel for detailed guidance*

##### Level 5: Help & Context

**Step 1 — Describe the Goal:** **What:** Define the primary objective of this process. **Why:** A well-defined goal limits the AI scope and ensures the automation has concrete boundaries. **How:** Formulate the objective and describe the current process being automated. Example: *"Generate a branded quarterly report PDF from raw spreadsheet data, with executive summary."* rather than *"Automate reporting."*

**Step 2 — Selecting the Upstream Router:** **What:** Select the table/system that feeds minor tasks into this workflow. **Why:** The CYAM platform uses centralized routing (e.g. Telegram /mtask) to feed data. Connected upstream systems must be explicitly mapped here so the AI builds the correct ingestion webhooks. **How:** Select the relevant upstream sources from the checkboxes.

**Steps 3-4 — Uploads (Bucket A vs. Bucket B):** **What:** Provide necessary context files to the system. **Why:** Bucket A files educate the AI while it writes the backend scripts, providing explicit examples of your logic. Bucket B files dictate exactly what End Users are forced to upload natively during the final deployed dashboard tool. **How:** Use the Drive Picker to select reference manuals for Bucket A. For Bucket B, type a structural requirement name and optionally attach an "Exemplar Template".

* **Chatbot Note:** Assist the WDE with goal refinement, trigger selection, and understanding the distinction between Bucket A and Bucket B.

---

### Level 3: Task 2 — Process Distillation

#### Level 4: Steps

1. **Step 1 — Raw Process Dump**
   - Dump your rough notes, email threads, or existing SOP here. Don't worry about formatting. The AI will distill it into a clean process and help you identify missing constraints.
   - Click "Distill Process" to run the extraction.
   - 📖 *See Help & Context panel for detailed guidance*
2. **Step 2 — Distilled Happy Path & Constraints**
   - Review the AI-extracted "Happy Path".
   - The AI identifies potential gaps in your process and generates highly relevant "What if...?" questions about edge cases and formatting restrictions. Answer them directly in the UI to strengthen your workflow.

##### Level 5: Help & Context

**Step 1 — What is Process Distillation?:** **What:** Converting raw notes and emails into an architectural SOP constraint. **Why:** LLM logic execution relies on mathematically concrete step-by-step logic, not human ambiguity. Handing it a rough mess guarantees failure. **How:** Paste email chains, raw SOPs, and notes directly into the dump box, then press Distill to let the AI organize it chronologically into the "Happy Path".

**Step 2 — Managing Edge Cases:** **What:** Systematically resolving vague failure modes before deployment. **Why:** If the edge cases are not codified into the backend, the workflow fails unexpectedly during runtime when users act randomly. **How:** Read the AI's "What if...?" questions generated below the Happy Path, and explicitly answer them. Your answers are dynamically compiled into the final specification architecture.

* **Chatbot Note:** Guide the WDE through process elicitation. Help identify missing inputs, edge cases, and quality controls.

---

### Level 3: Task 3 — CYAM Knowledge Integration

#### Level 4: Steps

1. **Step 1 — Automatic Dependency Scanner**
   - Click "Suggest Integrations". The AI cross-references your process against the CYAM Data Dictionary.
   - It suggests which CYAM Platform data structures (like Profiles, Metadata Library) are required. 
   - Choose whether each dependency is a "Definite Requirement", "Optional", or "Do Not Include".
   - 📖 *See Help & Context panel for detailed guidance*
2. **Step 2 — Ad-hoc Context Requirements**
   - Specify any additional raw files the End User will need to upload in Stage 3 (e.g., specific reports, meeting notes). We use plain Markdown files to prevent taxing the database with new schema creation.

##### Level 5: Help & Context

**Step 1 — Suggest Integrations:** **What:** Identifying structured internal CYAM Platform data needed by the workflow. **Why:** Complex workflows require overarching relational variables like Active Project data, User Persona data, etc. Identifying them now builds them into the final AI code context. **How:** Press "Suggest Integrations". The AI queries the CYAM Data Dictionary and returns standard tables. Review each and logically mark them as Definite, Optional, or Do Not Include.

**Step 2 — Ad-hoc Markdown Integrations:** **What:** Including specific textual reports as supplementary logic. **Why:** Sometimes a workflow needs a specific PDF report or meeting notes transcript without warranting a permanent, complex CYAM Database schema. **How:** Use the Drive Picker to select reference Markdown/Plain Text files that act as standard input definitions for the End User to replicate easily.

* **Chatbot Note:** Help the WDE understand which CYAM data structures are relevant to their goal. Explain the `data_dictionary.csv`.

---

### Level 3: Task 4 — Workflow Tier Assessment

#### Level 4: Steps

1. **Step 1 — Generate Comprehensive Summary & Evaluate Tier**
   - Click **Generate Comprehensive Summary & Evaluate Tier Assignment**.
   - The AI evaluates all gathered context (Goal, Distilled Process, and Knowledge Dependencies) and recommends an Organizational Scope Tier.
   - Example Tiers:
     - **Tier 1 (Standard):** Org-wide standards (brand voice, common templates).
     - **Tier 2 (Methodology):** High-value domain expertise (Default).
     - **Tier 3 (Personal):** Individual 'under-the-desk' automations.
2. **Step 2 — Confirm or Override**
   - Review the compiled **Comprehensive Summary** readout in the output box to confirm all logic was accurately aggregated.
   - Accept the suggested Tier or select "Other / Override" to explain why the AI missed the mark.

##### Level 5: Help & Context

**Step 1 — Generate Summary & Viability:** **What:** Computing the final comprehensive prompt and deriving its hierarchical tier. **Why:** We must confirm that all your tasks (1, 2, and 3) were securely aggregated and that the logic maps cleanly to a strategic CYAM tier. **How:** Press the Generate button. The AI reads all input states, calculates the optimal Tier mathematically based on scale, and prints the raw data verbatim into the textarea so you can audit what it built.

**Step 2 — Selecting the Tier:** **What:** Validating or overriding the automated categorization. **Why:** The AI's Tier dictates how strictly the created tool is safeguarded and deployed. Tier 1 implies rigid global distribution (High Quality), Tier 2 implies departmental execution, while Tier 3 gives maximum leniency to individual users. **How:** Review the evaluation payload. Assign the tier using the 4 options. **Note on Skill Storage Recommendation:** Here you define whether the AI creates a brand new Agent Skill (file) or intelligently merges this instruction payload into an *existing* Skill to prevent bloat. Choose "Integrate into Existing" if this supplements an existing process.

* **Chatbot Note:** Since the Chatbot is "Session-Aware", it has access to your actual Goal, Trigger, and Process via state injection. Ask the Chatbot directly if you're unsure which Tier perfectly matches your specific workflow payload!

---

## Context & Chatbot Delivery Summary

| Field | Value |
|---|---|
| `INSTALL_CHATBOT` | `true` |
| `chatbot_context_file` | `Context_Knowledge_WF1.md` |
| Context URLs | Listed in `metadata.json` |
