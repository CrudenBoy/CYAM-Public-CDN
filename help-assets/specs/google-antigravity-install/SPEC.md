---
spec_id: "google-antigravity-install"
spec_version: "1.0"
generated_by: "CYAM_Spec_Designer"
generated_date: "2026-03-23"
category: "Admin Console"
---

# Google AntiGravity Installation Guide

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
   * **macOS:** Open your browser and navigate to [AntiGravity Download Page](https://antigravity.google/download).
   * **Select Architecture:** Choose between **Apple Silicon** (M1/M2/M3/M4) or **Intel** based on your Mac's processor.
[/OS:macOS]
[OS:Windows]
1.  **Visit the Official Download Site**: Go to the Google AntiGravity download page.
    *   [OS:macOS] **macOS:** Open your browser and navigate to [AntiGravity Download Page](https://antigravity.google/download).
        *   **Select Architecture:** Choose between **Apple Silicon** (M1/M2/M3/M4) or **Intel** based on your Mac's processor. [/OS:macOS]
    *   [OS:Windows] **Windows:** Open your browser and navigate to [AntiGravity Download Page](https://antigravity.google/download).
        *   **Download Installer:** Click the **Download for Windows (64-bit)** button to get the `.exe` installer. [/OS:Windows]

2.  **Install the Application**: Proceed with the local installation for your specific operating system.
    *   [OS:macOS] **Deploy to Applications**: Locate the downloaded `.dmg` file, double-click it, and drag the AntiGravity icon into the Applications folder alias.
        *   **Drag and Drop**: Ensure you drag the icon completely into the target folder to initiate the copy process. [/OS:macOS]
    *   [OS:Windows] **Run the Installer**: Locate the downloaded `.exe` file and double-click it to start the installation wizard.
        *   **Installation Wizard**: Follow the on-screen prompts to complete the installation. [/OS:Windows]

3.  **Launch AntiGravity**: Start the newly installed IDE application.
    *   [OS:macOS] **Launch**: Open your Applications folder and double-click **Antigravity**.
        *   **Security Bypass:** If macOS asks if you are sure you want to open it (app downloaded from internet), click **Open**. [/OS:macOS]
    *   [OS:Windows] **Launch**: Open your Start Menu, search for **AntiGravity**, and click to launch it.
        *   **SmartScreen Bypass:** If Windows Defender SmartScreen prevents the app from starting, click **More info** and then **Run anyway**. [/OS:Windows]

##### Level 5: Help & Context

**Step 1 — Download Site:** If you don't have Antigravity installed already, let's begin with installing Antigravity. Currently the product is available for preview and you can use your personal Gmail account or supported Google Workspace organizational account to get started with it. Go to the downloads page and click on the appropriate operating system version that is applicable to your case.

**Step 2 — Installation:** Launch the application installer. For macOS, drag the application to the Applications folder. For Windows, launch the downloaded `.exe` installer wizard. This is the standard way to install software and ensures the app has the correct permissions to run.

**Step 3 — Security:** Once you have completed the installation, launch the Antigravity application. macOS Gatekeeper or Windows Defender SmartScreen will verify the app for your safety. Clicking "Open" (macOS) or "More info -> Run anyway" (Windows) white-lists the application for future use. You should see a welcome screen, please proceed with clicking on Next each time.

<div class="carousel-os-toggle" style="margin-top: 10px;">
  <button class="os-btn active" data-os="macOS">macOS</button>
  <button class="os-btn" data-os="Windows">Windows</button>
</div>

* **Carousel Item 1:** The download options on the official site.
* **Carousel Item 2:** Installing the AntiGravity application.

---

### Level 3: Task 2 — Launch and Configure Safety Settings

#### Level 4: Steps

1. **Select the Cog wheel**: Click the cog wheel icon in the top right corner of the IDE.

2. **Select Open AntiGravity User Settings**: Choose this option from the dropdown menu.

3. **Modify Settings**: This screen explains how safe the default settings are on the Agent Setting page. 
   * **Secure mode:** Enhanced security controls for the Agent, restricting external access.
   * **Review-driven development (recommended):** The agent will frequently ask for review. This is a good balance and the recommended one since it allows the agent to make a decision and come back to the user for approval.

##### Level 5: Help & Context

**Steps 1-3 — Configure Safety Settings:** How do you want to use the Antigravity agent? The autonomy policy defines how much control the AI agent has over your system. This is about giving the Agent the ability to execute commands (applications/tools) in your terminal (Always proceed vs Request review), Review policy (determining when the agent asks for plan reviews), and JavaScript Execution policy in the browser.<br><br>The 4 options on the left are specific settings for the terminal execution, review, and JavaScript execution policies.<br>• **Secure mode:** Enhanced security controls for the Agent, restricting external access.<br>• **Review-driven development (recommended):** The agent will frequently ask for review. This is a good balance and the recommended one since it allows the agent to make a decision and come back to the user for approval.<br>• **Agent-driven development:** The agent will never ask for review.<br>• **Custom configuration**<br><br>Remember that settings can be changed at any time via Antigravity User Settings (Cmd + ,).

* **Carousel Item 1:** Select the Cog wheel.
* **Carousel Item 2:** Select Open AntiGravity User Settings.
* **Carousel Item 3:** Modify settings.

---

### Level 3: Task 3 — Sign In and Authenticate

#### Level 4: Steps

1. **Press Sign up/Login**: Click the blue button in the top right to start the authentication process. It will say "Sign in" if this is your first time.

2. **Choose Sign In Method**: Choose to sign in with Google or use a GCP project instead.
   * **Note:** See the Help & Context section for details on the GCP Project option.

3. **Choose an Account**: Select your Google Account from the list.

4. **Press Sign In**: You will see a message "Make sure that you have downloaded the App from Google." Click the Sign In button.

5. **Authentication Success**: You will see a message "Google Antigravity: You have successfully authenticated."

##### Level 5: Help & Context

**Steps 1-5 — Sign In and Authenticate:** Now, you're ready to Sign in to Google. As mentioned earlier, Antigravity is available in preview mode. Sign in now with your account. This will open up the browser allowing you to sign in.<br><br>On successful authentication, you will see a success message and it will lead you back to the Antigravity application. Go with the flow. Finally, review the Terms of Use. You can make a decision if you'd like to opt-in or not and then click on Next. This will lead you to the moment of truth, where Antigravity will be waiting to collaborate with you.

**GCP Project:** This is a Google Cloud Platform project used for billing and API quota limits for Cloud services like Vertex AI, which AntiGravity connects to. 

* **Carousel Item 1:** Press Sign up/Login.
* **Carousel Item 2:** Choose sign in method.
* **Carousel Item 3:** Choose an Account.
* **Carousel Item 4:** Press Sign In.
* **Carousel Item 5:** Authentication Success.

---

### Level 3: Task 4 — Learn more about AntiGravity

#### Level 4: Steps

1. **Explore**: You have successfully configured the core of AntiGravity! Use the links in the Help & Context section or simply ask the Chatbot to learn more about optional setups, extensions, and browser automation. The Chatbot has full access to the complete AntiGravity knowledge base. Please see the links and videos in the Help & Context Section.

##### Level 5: Help & Context

**Step 1 — Learn more about AntiGravity:** There are two links you can use for further information about AntiGravity:<br>• **YouTube**: [YouTube Playlist](https://www.youtube.com/playlist?list=PLuT8wfgyV8tjGHAYNHJ9wPES3BEq-TnKN)<br>• **Codelabs**: [Getting Started Codelabs](https://codelabs.developers.google.com/getting-started-google-antigravity#0)

* **Video Link:** AntiGravity Tutorial Playlist