---
spec_id: "google-antigravity-install"
spec_version: "1.0"
generated_by: "CYAM_Spec_Designer"
generated_date: "2026-03-23"
category: "Developer Tools"
---

# Google AntiGravity macOS Installation Guide

## Level 1: Category
* **Category:** Developer Tools
* **Permissions:** All Users

---

> **📋 Organizational Protocol**
> If you are operating within an organization, your first action is to
> diplomatically contact your ICT department to inform them of the
> actions you are about to take: Installing the Google AntiGravity IDE.

---

## Level 2: Installation and Initial Setup
**Goal:** Successfully download, install, and configure Google AntiGravity on your Apple device to begin autonomous development.

### Level 3: Task 1 — Download the Installer

#### Level 4: Steps

1. **Visit the Official Download Site**: Go to the Google AntiGravity download page.
[OS:macOS]
   * **macOS:** Open your browser and navigate to `https://antigravity.google/download`.
   * **Select Architecture:** Choose between **Apple Silicon** (M1/M2/M3/M4) or **Intel** based on your Mac's processor.
[/OS:macOS]

##### Level 5: Help & Context

**Step 1 — Download Site:** Google AntiGravity is an AI-powered IDE. Ensure you download the version specifically for macOS to ensure compatibility with Apple's security features.

* **Carousel Item 1:** The macOS download options on the official site.
  (Media: `1_step_1_macOS.png`)

---

### Level 3: Task 2 — Run the Application Installer

#### Level 4: Steps

1. **Open the DMG File**: Locate the downloaded `.dmg` file in your Downloads folder and double-click it.

2. **Deploy to Applications**: Drag the AntiGravity icon into the Applications folder alias.
[OS:macOS]
   * **Drag and Drop**: Ensure you drag the icon completely into the target folder to initiate the copy process.
[/OS:macOS]

##### Level 5: Help & Context

**Step 2 — Installation:** Dragging the application to the Applications folder is the standard way to install software on macOS. This ensures the app has the correct permissions to run.

* **Carousel Item 1:** Dragging the AntiGravity icon into the Applications folder.
  (Media: `2_step_1_macOS.png`)

---

### Level 3: Task 3 — Initial Launch and Policy Setup

#### Level 4: Steps

1. **Launch AntiGravity**: Open your Applications folder and double-click **Antigravity**.
[OS:macOS]
   * **Security Bypass:** If macOS asks if you are sure you want to open it (app downloaded from internet), click **Open**.
[/OS:macOS]

2. **Welcome Screen**: On the "Welcome to Antigravity" screen, click **Next**.
   (Media: `3_step_1_macOS.png`)

3. **Configure Autonomy Policy**: Select your preferred agent execution policy.
[OS:macOS]
   * **Recommended:** Select **Review-driven development**. This allows the agent to propose terminal commands but requires your explicit approval before execution.
[/OS:macOS]
   (Media: `3_step_2_macOS.png`)

##### Level 5: Help & Context

**Step 1 — Security:** macOS Gatekeeper verifies apps for your safety. Clicking "Open" white-lists the application for future use.

**Steps 2-3 — Policy:** The autonomy policy defines how much control the AI agent has over your system. "Review-driven" is the safest starting point for most users.

* **Carousel Item 1:** The Welcome to AntiGravity screen.
  (Media: `3_step_1_macOS.png`)
* **Carousel Item 2:** Selecting the Autonomy Policy.
  (Media: `3_step_2_macOS.png`)

---

### Level 3: Task 4 — Authenticate your Account

#### Level 4: Steps

1. **Sign In**: Click the **Sign In** button to connect your Google Account.
   * **Account Type:** Use a personal Gmail account for public preview access.
   * **Authorization:** Accept the browser authentication prompt to link your IDE.

##### Level 5: Help & Context

**Step 1 — Authentication:** Signing in is required to activate the Gemini 3 Pro models and sync your preferences across devices.

---

### Level 3: Task 5 — Verify Installation

#### Level 4: Steps

1. **Open Terminal**: In the AntiGravity IDE, open the integrated terminal (`Ctrl + ` `).
2. **Check Version**: Type `agy --version` and press Enter.
3. **Success Output**: You should see a version string (e.g., `Antigravity CLI v1.20.6`).

##### Level 5: Help & Context

**Step 2 — CLI Check:** The `agy` tool is the heart of AntiGravity's agentic power. Running this command confirms the CLI was installed correctly during the setup phase.

---

## Context & Chatbot Delivery Summary

| Field | Value |
|---|---|
| `INSTALL_CHATBOT` | `true` |
| `chatbot_context_file` | `Google_AntiGravity_Context_Knowledge.md` |
| Context URLs | Listed in `metadata.json` |
