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

**Step 1 — Writing a Strong Goal:** A well-defined goal is the most critical input. Be specific about the *end result* you want — not just the process. Example: *"Generate a branded quarterly report PDF from raw spreadsheet data, with executive summary and data visualizations"* is better than *"Automate reporting."*

**Step 2 — Understanding Triggers:** Triggers define how the workflow will be started by the End User:
- **Webhook** — Triggered by an external system sending an HTTP request.
- **Schedule** — Runs on a timer (daily, weekly, etc.).
- **AppSheet Button** — Triggered from a mobile/tablet interface.
- **Manual** — WDE or End User explicitly starts it from the Dashboard.

**Steps 3-4 — Two Buckets of Uploads:** Your uploads serve two distinct purposes:
- **Bucket A (Spec-Writing):** Material that helps the AI understand what you're building. Examples: your current manual process document, competitor workflow screenshots, domain-specific reference material.
- **Bucket B (Stage 3 Requirements):** A specification of what the *End User* needs to provide later. You define the types and formats required. The End User supplies their own real data in Stage 3.

* **Chatbot Note:** Assist the WDE with goal refinement, trigger selection, and understanding the distinction between Bucket A (spec-writing material) and Bucket B (End User requirements). Help clarify what constitutes a "definite" vs "optional" requirement.

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

**What is Process Distillation?:** Don't overthink the initial step. Write the process as you would explain it to a colleague. The AI analyzes the intent and ensures you don't miss critical process elements like missing inputs or ambiguous deliverables.

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

**Understanding CYAM Data Structures:** The CYAM Platform stores structured data in Google Sheets tables (Profiles, Plans, Metadata Library). When you select a structure here, you are telling the specification: *"This workflow needs this data."* The End User supplies the real data in Stage 3.

**Definite vs Optional:** Mark a dependency as "Definite Requirement" only if the workflow **cannot function** without it. Mark as "Optional" if it improves output quality but isn't strictly required.

* **Chatbot Note:** Help the WDE understand which CYAM data structures are relevant to their goal. Explain the `data_dictionary.csv`.

---

### Level 3: Task 4 — Workflow Tier Assessment

#### Level 4: Steps

1. **Step 1 — Evaluate Tier Assignment**
   - The AI evaluates all gathered context (Goal, Distilled Process, and Knowledge Dependencies) and recommends an Organizational Scope Tier.
   - Example Tiers:
     - **Tier 1 (Standard):** Org-wide standards (brand voice, common templates).
     - **Tier 2 (Methodology):** High-value domain expertise (Default).
     - **Tier 3 (Personal):** Individual 'under-the-desk' automations.
2. **Step 2 — Confirm or Override**
   - Accept the suggested Tier or select "Other / Override" to explain why the AI missed the mark.

##### Level 5: Help & Context

**What Tier Means:** The Tier determines how the AI guides you through the remaining Workflows:
- **Tier 1:** Autonomous scaling works well.
- **Tier 2:** Domain expertise is critical. High-value.
- **Tier 3:** Useful for specific users, but won't be pushed globally.

* **Chatbot Note:** Since the Chatbot is "Session-Aware", it has access to your actual Goal, Trigger, and Process via state injection. Ask the Chatbot directly if you're unsure which Tier perfectly matches your specific workflow payload!

---

## Context & Chatbot Delivery Summary

| Field | Value |
|---|---|
| `INSTALL_CHATBOT` | `true` |
| `chatbot_context_file` | `Context_Knowledge_WF1.md` |
| Context URLs | Listed in `metadata.json` |
