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

### Level 3: Task 2 — Workflow Tier Assessment

#### Level 4: Steps

1. **Step 1 — Review AI Tier Suggestion**
   - The AI analyses your Goal from Task 1 and recommends a Tier:
     - **Tier 1 (Routine):** Simple, repeatable processes with clear inputs/outputs.
     - **Tier 2 (Methodology):** Domain-specific processes requiring expert knowledge and edge case handling.
     - **Tier 3 (Enterprise):** Cross-functional, multi-stakeholder processes with compliance requirements.
   - Review the AI's rationale card below.
   - 📖 *See Help & Context panel for detailed guidance*
2. **Step 2 — Confirm or Override**
   - Accept the suggested Tier, or override it with your own classification.
   - If overriding, provide a brief justification (e.g., *"This is Tier 3 because it crosses compliance boundaries"*).
   - 📖 *See Help & Context panel for detailed guidance*

##### Level 5: Help & Context

**Step 1 — What Tier Means:** The Tier determines how the AI guides you through the remaining Workflows:
- **Tier 1:** Mode A (Autonomous) works well. The AI can handle most decisions.
- **Tier 2:** Mode B (Cyborg) strongly recommended for Workflows 2 & 3. Your domain expertise is critical.
- **Tier 3:** Mode B is mandatory. Every decision requires human validation before the AI proceeds.

**Step 2 — When to Override:** Override if you have domain knowledge the AI can't infer from your goal description. For example, a workflow that sounds simple ("send an email") may actually be Tier 3 if it involves regulated communications or multi-approval chains.

* **Chatbot Note:** Help the WDE understand Tier implications for their specific workflow. Clarify Mode A vs Mode B recommendations and what "domain expertise" means in context.

---

### Level 3: Task 3 — Current Mechanics & SOPs

#### Level 4: Steps

1. **Step 1 — Outline the Process**
   - Describe the current manual process in the text area below. Focus on capturing the flow, not perfecting prose.
   - The primary objective is to **outline the process** — not deliver a polished document.
   - 📖 *See Help & Context panel for detailed guidance*
2. **Step 2 — Upload Example SOP (Optional)**
   - If you have an existing SOP or process document, upload it via the Google Drive Picker.
   - This is a reference input — the AI uses it to inform the specification. It is not required.
   - 📖 *See Help & Context panel for detailed guidance*
3. **Step 3 — Guided Process Elicitation (If No SOP)**
   - If no SOP exists, use the structured scaffolding form below:
     - **Inputs:** What enters the process? (data, files, approvals)
     - **Activities:** What transforms the inputs? (calculations, reviews, decisions)
     - **Outputs:** What is produced? (reports, notifications, approvals)
     - **Controls:** What ensures quality? (validation rules, approval gates, thresholds)
   - 📖 *See Help & Context panel for detailed guidance*

##### Level 5: Help & Context

**Step 1 — Process Outline Tips:** Don't overthink it. Write the process as you would explain it to a colleague: *"First we receive X, then Y checks it, then Z approves it."* The AI will structure it formally later.

**Step 2 — SOP as Reference:** An existing SOP helps the AI understand your domain vocabulary and edge cases. If you upload one, the AI extracts the logic — it doesn't copy the document wholesale.

**Step 3 — ISO 9001 Thinking:** The Inputs → Activities → Outputs → Controls framework comes from ISO 9001 quality management. It ensures you don't miss critical process elements:
- **Inputs:** Raw materials the process needs (data, documents, triggers).
- **Activities:** The work that transforms inputs into outputs.
- **Outputs:** The deliverables — what success looks like.
- **Controls:** Quality gates ensuring outputs meet standards.

* **Chatbot Note:** Guide the WDE through process elicitation using the ISO 9001 IAOC framework. Help identify missing inputs, edge cases, and quality controls.

---

### Level 3: Task 4 — CYAM Knowledge Integration

#### Level 4: Steps

1. **Step 1 — Review AI-Suggested Dependencies**
   - The AI reads the `data_dictionary.csv` and, based on your Goal from Task 1, suggests which CYAM Platform data structures are relevant for the workflow you are creating.
   - Suggestions may include: Profile tables, Plan table, Metadata_Library, File_Library, System_FolderMap.
   - Review the suggestion cards below. Confirm, remove, or add to the list.
   - 📖 *See Help & Context panel for detailed guidance*
2. **Step 2 — Classify as Definite or Optional**
   - For each selected dependency, mark it as:
     - **Definite** — The End User *must* provide this data in Stage 3.
     - **Optional** — Recommended to optimise the workflow prompt.
   - 📖 *See Help & Context panel for detailed guidance*
3. **Step 3 — Define Additional Stage 3 Context Files**
   - Beyond CYAM data structures, specify any additional raw files the End User will need to upload in Stage 3 (e.g., spreadsheets, PDFs, presentations).
   - For each, describe the expected content and format.
   - 📖 *See Help & Context panel for detailed guidance*
4. **Step 4 — Define Conversion Rules**
   - Specify how raw End User files will be converted into structured Markdown context files usable by the workflow's nodes.
   - Optionally upload template Markdown files demonstrating the expected output structure.
   - 📖 *See Help & Context panel for detailed guidance*

##### Level 5: Help & Context

**Step 1 — Understanding CYAM Data Structures:** The CYAM Platform stores structured data in Google Sheets tables (Profiles, Plans, Metadata Library) and in the Google Drive folder structure (File Library, System folders). When you select a structure here, you are telling the specification: *"This workflow needs this data."* The End User provides their own data in Stage 3.

**Step 2 — Definite vs Optional:** Mark a dependency as "Definite" only if the workflow **cannot function** without it. Mark as "Optional" if it improves output quality but isn't strictly required. This helps End Users understand the minimum viable setup vs the optimised setup.

**Steps 3-4 — Raw File Conversion:** Most workflows will need End Users to upload raw files (DOCX, PDF, Google Sheets) that aren't already in the CYAM data structures. The conversion rules you define here tell the workflow how to transform those raw files into structured Markdown that the AI can consume. Upload template examples showing the expected Markdown structure.

* **Chatbot Note:** Help the WDE understand which CYAM data structures are relevant to their goal. Explain the `data_dictionary.csv` suggestions. Guide them in writing conversion rules and creating Markdown template examples.

---

## Context & Chatbot Delivery Summary

| Field | Value |
|---|---|
| `INSTALL_CHATBOT` | `true` |
| `chatbot_context_file` | `Context_Knowledge_WF1.md` |
| Context URLs | Listed in `metadata.json` |
