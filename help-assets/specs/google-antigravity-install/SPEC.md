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

**Prerequisites** 
- Node.js installed (verified via `node -v`).
- **Google Cloud CLI (gcloud)** installed and authenticated.
- Access to a Google Workspace account.

#### Level 4: Steps

1. **Visit the Official Download Site**: Go to the Google AntiGravity download page.

[OS:macOS]
* **macOS:** Open your browser and navigate to [AntiGravity Download Page](https://antigravity.google/download).
  * **Select Architecture:** Choose between **Apple Silicon** (M1/M2/M3/M4) or **Intel** based on your Mac's processor.
[/OS:macOS]

[OS:Windows]
* **Windows:** Open your browser and navigate to [AntiGravity Download Page](https://antigravity.google/download).
  * **Download Installer:** Click the **Download for Windows (64-bit)** button to get the `.exe` installer.
[/OS:Windows]

2. **Install the Application**: Proceed with the local installation for your specific operating system.

[OS:macOS]
* **Deploy to Applications**: Locate the downloaded `.dmg` file, double-click it, and drag the AntiGravity icon into the Applications folder alias.
  * **Drag and Drop**: Ensure you drag the icon completely into the target folder to initiate the copy process.
[/OS:macOS]

[OS:Windows]
* **Run the Installer**: Locate the downloaded `.exe` file and double-click it to start the installation wizard.
  * **Installation Wizard**: Follow the on-screen prompts to complete the installation.
[/OS:Windows]

3. **Launch AntiGravity**: Start the newly installed IDE application.

[OS:macOS]
* **Launch**: Open your Applications folder and double-click **Antigravity**.
  * **Security Bypass:** If macOS asks if you are sure you want to open it (app downloaded from internet), click **Open**.
[/OS:macOS]

[OS:Windows]
* **Launch**: Open your Start Menu, search for **AntiGravity**, and click to launch it.
  * **SmartScreen Bypass:** If Windows Defender SmartScreen prevents the app from starting, click **More info** and then **Run anyway**.
[/OS:Windows]

##### Level 5: Help & Context

**Step 1 — Download Site:** If you don't have Antigravity installed already, let's begin with installing Antigravity. Currently the product is available for preview and you can use your personal Gmail account or supported Google Workspace organizational account to get started with it. Go to the downloads page and click on the appropriate operating system version that is applicable to your case.

**Step 2 — Installation:** Launch the application installer. For macOS, drag the application to the Applications folder. For Windows, launch the downloaded `.exe` installer wizard. This is the standard way to install software and ensures the app has the correct permissions to run.

**Step 3 — Security:** Once you have completed the installation, launch the Antigravity application. macOS Gatekeeper or Windows Defender SmartScreen will verify the app for your safety. Clicking "Open" (macOS) or "More info -> Run anyway" (Windows) white-lists the application for future use. You should see a welcome screen, please proceed with clicking on Next each time.

<div class="carousel-os-toggle" style="margin-top: 10px;">
  <button class="os-btn active" data-os="macOS">macOS</button>
  <button class="os-btn" data-os="Windows">Windows</button>
</div>

* **Carousel Item 1:** Visit the official download page. (Media: `1_step_1_macOS.png` / `1_step_1.0_Windows.png`)
* **Carousel Item 2:** View the installation folder UI. (Media: `2_step_1_macOS.png` / `1_step_1.2_Windows.png`)

---

### Level 3: Task 2 — Install Google Workspace CLI

#### Level 4: Steps

<details>
<summary>🤖 AntiGravity Agent Prompt</summary>

If you prefer to have an AI agent perform the technical parts of this setup, you can use the prompt below. AntiGravity will use the existing `SKILL.md` to guide you through Tasks 2 to 6, stopping only when your manual input (like choosing a Google account) is required.

**Recommended Prompt:**

> "Please refer to the SKILL.md saved to the GitHub CDN repo at https://raw.githubusercontent.com/CrudenBoy/CYAM-Public-CDN/main/help-assets/specs/google-antigravity-install/SKILL.md and assist me with the Google Workspace CLI setup (Tasks 2 to 5). Start by verifying the installation of Node.js and then proceed to install the CLI. Guide me through the Google Cloud Console steps by providing the exact URLs, and then resume the technical configuration once I have my Client ID and Secret."

</details>

1. **Open Your Terminal**: Launch your system's command-line interface.

[OS:macOS]
* **macOS (Terminal):**
  * Press **Cmd + Space**, type 'Terminal', and press Enter.
[/OS:macOS]

[OS:Windows]
* **Windows (PowerShell/CMD):**
  * Search for 'PowerShell' in the Start menu. Right-click it and select **"Run as Administrator"**.
[/OS:Windows]

2. **Install the Package**: Run the following command exactly:

[OS:macOS]
```bash
sudo npm install -g @googleworkspace/cli
```
[/OS:macOS]

[OS:Windows]
```powershell
npm install -g @googleworkspace/cli
```
[/OS:Windows]

3. **Verify Installation**: Wait for the process to finish, then verify by typing:

[OS:macOS]
```bash
gws --version
```
[/OS:macOS]

[OS:Windows]
```powershell
gws --version
```
[/OS:Windows]

##### Level 5: Help & Context

**Installation Nuances:** The installation requires global permissions because `npm` writes to protected system folders. On Windows, if you see `EPERM` errors, it’s almost always because the terminal wasn't opened as Administrator. On macOS, prepending the command with `sudo` is the standard fix.

---

### Level 3: Task 3 — Google Cloud Console Setup (Manual Task)

> [!NOTE]
> This task must be performed by a human in a web browser because it involves security settings and 2FA.

#### Level 4: Steps

1. **Open/Create Your Project**:
   * Go to the [Google Cloud Console](https://console.cloud.google.com/).
   * Click the **Project Dropdown** at the top left.
   * Select an existing project (e.g., `cyam-workspace-cli`) or click **New Project** to create one.

2. **Enable APIs and Services**:
   * Use the search bar at the top to find and **Enable** each of these APIs:
     * **Gmail API** (Essential for email-to-sheet workflows)
     * **Google Sheets API** (Essential for creating/editing spreadsheets)
     * **Google Drive API** (Core requirement for most GWS tasks)
     * **Google Calendar API** (Optional)
     * **Google Docs API** (Optional)

3. **Configure OAuth Consent Screen**:
   * Search for **"OAuth consent screen"** in the top search bar.
   * Click **Get Started**.
   * Click **Create**.
   * Fill in the **App Information**:
     * **App name**: "GWS CLI"
     * **User support email**: Your email address.
   * Select Audience: Select **Internal** (if you have a Workspace organization) or **External** (if using a personal @gmail.com account).
   * Add Contact Information:
     * **Developer contact info**: Your email address.
   * Click **Finish** through the remaining screens. You will be taken to Step 4 to configure **OAuth client ID**.

4. **Create Desktop Credentials**:
   * After completing Step 3, you will be taken to the **Application type** screen. Alternatively, search for **"Credentials"** in the top search bar.
   * Click **+ Create Credentials** > **OAuth client ID**.
   * **Application type**: Select **Desktop app**.
   * **Name**: example "GWS CLI Desktop".
   * Click **Create**.
   * **Save these!** Copy the **Client ID** and **Client Secret** to a safe place; you will need them for the next task.

##### Level 5: Help & Context

**Why This is Manual:** Google Cloud Platform enforces strict security. Enabling APIs is like "unlocking doors" for the CLI tool. If you skip enabling the Gmail API, for example, the CLI will be "Authorized" to talk to your account but "Forbidden" from actually reading emails.

---

### Level 3: Task 4 — CLI Authorization Setup

#### Level 4: Steps

1. **Start CLI Setup**: In your terminal, run the setup command:

[OS:macOS]
```bash
gws auth setup --project your-project-id
```
[/OS:macOS]

[OS:Windows]
```powershell
gws auth setup --project your-project-id
```
[/OS:Windows]

*(Replace `your-project-id` with the ID of the project you created/selected in Task 3).*

2. **Input Credentials**: When prompted, paste the **Client ID** and **Client Secret** you saved from Task 3.

---

### Level 3: Task 5 — Complete OAuth Login & Scopes

#### Level 4: Steps

1. **Run Login Command**: Run the following command to grant the CLI access to your data:

[OS:macOS]
```bash
gws auth login -s drive,gmail,sheets
```
[/OS:macOS]

[OS:Windows]
```powershell
gws auth login -s drive,gmail,sheets
```
[/OS:Windows]

2. **Select Scopes in Terminal**: Use the arrow keys and **Space** to ensure these are checked:
   * [x] **Recommended (Core Consumer Scopes)**
   * [x] **gmail.readonly**
   * [x] **spreadsheets**
   * Press **Enter**.

3. **Approve in Browser**:
   * A browser window will open. Select your Google account.
   * **CRITICAL:** You must **manually check the boxes** for Gmail, Sheets, and Drive on the "GWS CLI wants to access your account" screen.
   * Click **Allow**.

---

### Level 3: Task 6 — Verification

#### Level 4: Steps

1. **Test Drive Access**: Validate that the CLI can see your files:

[OS:macOS]
```bash
gws drive files list --params '{"pageSize": 5}'
```
[/OS:macOS]

[OS:Windows]
```powershell
gws drive files list --params "{\`"pageSize\`": 5}"
```
[/OS:Windows]

2. **Test Gmail/Sheets Integration**: Run a test to ensure the CLI can read emails and write to a sheet. *(If you have a script for this, run it now, otherwise manually verify you can see your file list).*

##### Level 5: Help & Context

**Resources:**
- [Official GWS CLI Documentation](https://googleworkspace-cli.mintlify.app/)
- [Google Cloud Console](https://console.cloud.google.com/)
- [Gmail API Scopes Reference](https://developers.google.com/gmail/api/auth/scopes)

---

## Context & Chatbot Delivery Summary

### Overview: GWS CLI Technical Architecture

The `gws` CLI is a cross-platform tool that communicates with Google Workspace APIs via OAuth 2.0. It requires a Desktop-type OAuth Client ID associated with a GCP project where the relevant APIs (Drive, Gmail, Sheets) are enabled.

### Implementation Details

- **Configuration Storage**: Settings are stored in `$HOME/.config/gws/`.
- **Token Management**: OAuth tokens are encrypted and cached in `token_cache.json`.
- **Scope Requirements**: Core tasks require `https://www.googleapis.com/auth/drive`, `https://www.googleapis.com/auth/gmail.readonly`, and `https://www.googleapis.com/auth/spreadsheets`.

### Edge Cases & Troubleshooting

| Issue | Likely Cause | Resolution |
| :--- | :--- | :--- |
| `403 Forbidden` | API not enabled in GCP | Go to Library and enable the specific API. |
| `insufficientPermissions` | Scopes not checked in browser | Re-run `gws auth login` and check all boxes. |
| `Connection Refused` | CLI listener timeout | Restart the login command and refresh browser. |
| `EPERM` (Windows) | Missing Admin rights | Restart terminal as "Run as Administrator". |

### Q&A

**Q: Can I use the same Client ID for multiple users?**
A: Yes, the Client ID identifies the *application* (the CLI), while the login process identifies the *user*.

**Q: How do I change the project after setup?**
A: Run `gws auth setup --project new-project-id` to overwrite the existing configuration.

### Key Links

* **Official Docs:** [https://googleworkspace-cli.mintlify.app/](https://googleworkspace-cli.mintlify.app/)  
* **GitHub Repository:** [https://github.com/googleworkspace/cli](https://github.com/googleworkspace/cli)  
* **NPM Package:** [https://www.npmjs.com/package/@googleworkspace/cli](https://www.npmjs.com/package/@googleworkspace/cli)  
* **Video Tutorial (Fru Dev):** [https://www.youtube.com/watch?v=aci6mSkFPf8](https://www.youtube.com/watch?v=aci6mSkFPf8)