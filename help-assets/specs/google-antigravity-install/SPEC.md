---
spec_id: "google-antigravity-install"
spec_version: "1.0"
generated_by: "CYAM_Spec_Designer"
generated_date: "2026-03-23"
category: "Admin Console"
---

# Google AntiGravity macOS Installation Guide

## Level 1: Category
* **Category:** Admin Console
* **Permissions:** All Users

---

> **📋 Organizational Protocol**
> If you are operating within an organization, your first action is to
> diplomatically contact your ICT department to inform them of the
> actions you are about to take: Installing the Google AntiGravity IDE.

---

## Level 2: Installation and Initial Setup
**Goal:** Successfully download, install, and configure Google AntiGravity on your Apple device to begin autonomous development.

### Level 3: Task 1 — Download and Install Antigravity

#### Level 4: Steps

1. **Visit the Official Download Site**: Go to the Google AntiGravity download page.
[OS:macOS]
   * **macOS:** Open your browser and navigate to `https://antigravity.google/download`.
   * **Select Architecture:** Choose between **Apple Silicon** (M1/M2/M3/M4) or **Intel** based on your Mac's processor.
[/OS:macOS]

2. **Deploy to Applications**: Locate the downloaded `.dmg` file, double-click it, and drag the AntiGravity icon into the Applications folder alias.
[OS:macOS]
   * **Drag and Drop**: Ensure you drag the icon completely into the target folder to initiate the copy process.
[/OS:macOS]

##### Level 5: Help & Context

**Step 1 — Download Site:** If you don't have Antigravity installed already, let's begin with installing Antigravity. Currently the product is available for preview and you can use your personal Gmail account or supported Google Workspace organizational account to get started with it. Go to the downloads page and click on the appropriate operating system version that is applicable to your case.

**Step 2 — Installation:** Launch the application installer and install the same on your machine by dragging the application to the Applications folder. This is the standard way to install software on macOS and ensures the app has the correct permissions to run.

* **Carousel Item 1:** The macOS download options on the official site.
  (Media: `1_step_1_macOS.png`)
* **Carousel Item 2:** Dragging the AntiGravity icon into the Applications folder.
  (Media: `2_step_1_macOS.png`)

---

### Level 3: Task 2 — Launch and Configure Safety Settings

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

**Step 1 — Security:** Once you have completed the installation, launch the Antigravity application. macOS Gatekeeper verifies apps for your safety. Clicking "Open" white-lists the application for future use. You should see a welcome screen, please proceed with clicking on Next each time.

**Steps 2-3 — Policy:** How do you want to use the Antigravity agent? The autonomy policy defines how much control the AI agent has over your system. This is about giving the Agent the ability to execute commands (applications/tools) in your terminal (Always proceed vs Request review), Review policy (determining when the agent asks for plan reviews), and JavaScript Execution policy in the browser.<br><br>The 4 options on the left are specific settings for the terminal execution, review, and JavaScript execution policies.<br>• **Secure mode:** Enhanced security controls for the Agent, restricting external access.<br>• **Review-driven development (recommended):** The agent will frequently ask for review. This is a good balance and the recommended one since it allows the agent to make a decision and come back to the user for approval.<br>• **Agent-driven development:** The agent will never ask for review.<br>• **Custom configuration**<br><br>Remember that settings can be changed at any time via Antigravity User Settings (Cmd + ,).

* **Carousel Item 1:** The Welcome to AntiGravity screen.
  (Media: `3_step_1_macOS.png`)
* **Carousel Item 2:** Selecting the Autonomy Policy.
  (Media: `3_step_2_macOS.png`)

---

### Level 3: Task 3 — Sign In and Authenticate

#### Level 4: Steps

1. **Sign In**: Click the **Sign In** button to connect your Google Account.
   * **Account Type:** Use a personal Gmail account or supported Google Workspace organizational account.
   * **Authorization:** Accept the browser authentication prompt to link your IDE.

2. **Learn more about AntiGravity**: You have successfully configured the core of AntiGravity! 
   * **Explore**: Use the links in the Help & Context section or simply ask the Chatbot to learn more about optional setups, extensions, and browser automation. The Chatbot has full access to the complete AntiGravity knowledge base.

##### Level 5: Help & Context

**Step 1 — Authentication:** Now, you're ready to Sign in to Google. As mentioned earlier, Antigravity is available in preview mode. Sign in now with your account. This will open up the browser allowing you to sign in.<br><br>On successful authentication, you will see a success message and it will lead you back to the Antigravity application. Go with the flow. Finally, review the Terms of Use. You can make a decision if you'd like to opt-in or not and then click on Next. This will lead you to the moment of truth, where Antigravity will be waiting to collaborate with you.

**Step 2 — Further Information:** There are two links you can use for further information about AntiGravity:<br>• **YouTube**: https://www.youtube.com/playlist?list=PLuT8wfgyV8tjGHAYNHJ9wPES3BEq-TnKN<br>• **Codelabs**: https://codelabs.developers.google.com/getting-started-google-antigravity#0

---

## Context & Chatbot Delivery Summary

| Field | Value |
|---|---|
| `INSTALL_CHATBOT` | `true` |
| `chatbot_context_file` | `Google_AntiGravity_Context_Knowledge.md` |
| Context URLs | Listed in `metadata.json` |
