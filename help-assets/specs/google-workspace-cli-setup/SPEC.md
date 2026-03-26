---
spec_id: "google-workspace-cli-setup"
spec_version: "1.0"
generated_by: "CYAM_Spec_Designer"
generated_date: "2026-03-18"
category: "CLI Setup and Authentication"
---

# Google Workspace CLI Setup Guide

## Level 1: Category
* **Category:** CLI Setup and Authentication
* **Permissions:** All Users

---

> **📋 Organizational Protocol**
> If you are operating within an organization, your first task is to diplomatically contact your ICT department to inform them that you will be creating a local Google Cloud Project and OAuth credentials to authenticate a local automation tool (Google Workspace CLI).

---

## Level 2: Setting up the Google Cloud and Workspace command-line tools for local automation
**Goal:** To allow the CYAM platform and AI agents to help manage your Google Workspace (Drive, Gmail, Calendar, Docs, etc.), we need to install two helper tools on your computer. First, we install the Google Cloud CLI to manage your Google Cloud account. Second, we install the Google Workspace CLI (gws) which acts as the bridge. We then create a dedicated 'CYAM-Workspace-CLI' project in Google Cloud, configure the Open Authorization (OAuth) security settings, and finally log in. This securely connects your tools without exposing your passwords. (Overview Media: `overview_animation.webp`)


### Level 3: Task 1 — Install Google Cloud CLI

**Prerequisites** 
- Node.js installed (verified via `node -v`).
- **Google Cloud CLI (gcloud)** installed and authenticated.
- Access to a Google Workspace account.

#### Level 4: Steps

1. Your computer must have **Node.js** installed to download the Workspace CLI. Node.js is an underlying software platform. If you do not have it, download and install it from the [official Node.js website](https://nodejs.org/).

<details>
<summary>🤖 Agent Automation</summary>

> "Please install Node.js and the latest version of Python 3 for me."

</details>

2. **Check Python Version**: The CLI requires Python.
[OS:macOS]
   * **macOS:** Open Terminal. Type `python3 -V` and press Enter.
[/OS:macOS]
[OS:Windows]
   * **Windows:** Open PowerShell (press `Win + X` and select "Windows PowerShell"). Type `python -V` and press Enter.
   * If `python` opens the Microsoft Store instead of showing a version, Python is not installed. Download it from [python.org](https://www.python.org/downloads/).
   * **CRITICAL (Windows):** During Python installation, on the very first screen check the box labelled **"Add Python to PATH"**. Without this, the `python` command won't work.
   * After installing, **close and reopen PowerShell** before retrying `python -V`.
[/OS:Windows]
   * If it prints a version number (like Python 3.x.x), you are ready. If you get an error, download Python from python.org.

3. **Download the Installer**: Go to the [Google Cloud CLI Downloads](https://cloud.google.com/sdk/docs/install) page.
[OS:macOS]
   * **macOS:** Check your chip type (Apple Silicon/M1/M2/M3 vs Intel) by clicking the Apple Logo > About This Mac. Download the matching macOS archive.
[/OS:macOS]
[OS:Windows]
   * **Windows:** Download the **Windows 64-bit (bundled Python)** `.exe` installer. This version includes Python and handles all dependencies automatically. Most modern Windows 10/11 systems are 64-bit.
[/OS:Windows]

4. **Extract the Download**:
[OS:macOS]
   * **macOS:** Find the downloaded `.tar.gz` file in your Downloads folder and double-click it to extract a folder named `google-cloud-sdk`.
[/OS:macOS]
[OS:Windows]
   * **Windows:** Right-click the downloaded `.exe` file and select **"Run as administrator"**. If Windows Security shows "Windows protected your PC", click **"More info"** then **"Run anyway"** (this is normal for new installers).
[/OS:Windows]

5. **Run the Installer**:
[OS:macOS]
   * **macOS:** Open the **Terminal** application. Drag and drop the `install.sh` file from inside that `google-cloud-sdk` folder directly into the Terminal window and press Enter. 
     * It will ask: "Do you want to help improve the Google Cloud CLI (y/N)?". Type **N** and press Enter.
     * It will ask: "Modify profile to update your $PATH...? (Y/n)?". Type **Y** and press Enter.
     * It will ask: "Enter a path to an rc file to update, or leave blank to use...". **Just press the Enter key** to accept the default.
     * **INVISIBLE PASSWORD PROMPT**: If the terminal says "Running Python 3.13 installer, you may be prompted for sudo password..." followed by a `Password:` prompt, it needs your Mac computer login password to install Python. Type your password and press Enter. **Crucial Note:** As you type, the keys will not show up on the screen (no asterisks). Just type it blindly and press Enter.
[/OS:macOS]
[OS:Windows]
   * **Windows:** Follow the installation wizard:
     1. **Welcome Screen**: Click "Next".
     2. **License Agreement**: Click "I Agree".
     3. **Installation Type**: Choose "Install for all users" if you have admin rights.
     4. **Component Selection**: Ensure **"Google Cloud CLI Core Libraries"** and **"Bundled Python"** are both checked.
     5. **Installation Options**: **CRITICAL** — Check both **"Start Google Cloud CLI Shell"** and **"Run `gcloud init`"**.
     6. Click "Install" and wait 2-5 minutes for completion.
   * After installation, the **Google Cloud SDK Shell** should open automatically — keep it open for the next step.
[/OS:Windows]

6. **Log In and Initialize**: 
   * Open a fresh, new Terminal (macOS) or PowerShell (Windows).
   * Type exactly: `gcloud init` and press Enter. 
   * **Configuration Prompt**: If it says "Pick configuration to use", type **1** (Re-initialize) and press Enter.
   * **Account Prompt**: If it says "Choose the account you want to use", and your desired email is listed, type the number next to your email (e.g. **1**) and press Enter. **Important Note on Passkeys:** If you use a passkey (Fingerprint/FaceID) to log into Google, do not select an existing account here, because the terminal cannot prompt for passkeys. Instead, select the number for **"Sign in with a new Google Account"** which will safely open your web browser to handle the passkey.
   * If you chose to sign in, a browser window will pop up. Log into your Google Account and click "Allow" to grant access.
   * Back in the terminal, it asks you to **"Pick cloud project to use"**. Look down the list for the number next to **Create a new project** (for example, `[38]`). Type that exact number and press Enter.
   * It will ask for a Project ID. Type `cyam-workspace-cli` (if it says it's taken, add some random numbers to the end) and press Enter.
   * The terminal will say **"The Google Cloud CLI is configured and ready to use!"** You are done with gcloud!

##### Level 5: Help & Context

**Step 1 — Node.js:** Node.js is a software platform that the Workspace CLI runs on. You only need to install it once. Download the **LTS** version from [nodejs.org](https://nodejs.org/). After installing, open a **new** terminal and type `node -v` to verify.

**Step 2 — Python Check:** Google Cloud CLI requires Python 3.8+. On macOS, type `python3 -V`. On Windows, type `python -V`. If Python isn't found or opens the Microsoft Store, install it from [python.org](https://www.python.org/downloads/) — **check "Add Python to PATH" during install**.

**Step 3 — Download:** Go to the [Google Cloud CLI Downloads](https://cloud.google.com/sdk/docs/install) page. On macOS, check Apple Menu > About This Mac to determine if you need the Apple Silicon or Intel version. On Windows, choose the **bundled Python** `.exe` installer.

**Step 4 — Extract:** On macOS, double-click the `.tar.gz` file in your Downloads folder to extract a `google-cloud-sdk` folder. On Windows, right-click the `.exe` and select "Run as administrator".

**Step 5 — Run Installer:** On macOS, drag `install.sh` from the extracted folder into Terminal and press Enter. Answer N to usage stats, Y to PATH update, and just press Enter for the rc file path. On Windows, follow the wizard — ensure both "Start Cloud SDK Shell" and "Run gcloud init" are checked.

**Step 6 — Initialize:** In a fresh terminal, run `gcloud init`. Choose "Re-initialize" (option 1), then "Sign in with a new Google Account" (avoids passkey issues). Log in via browser, then create a new project named `cyam-workspace-cli`.


<div class="carousel-os-toggle" style="margin-top: 10px;">
  <button class="os-btn active" data-os="macOS">macOS</button>
  <button class="os-btn" data-os="Windows">Windows</button>
</div>

* **Carousel Item 1:** Download and install Node.js (required prerequisite). (Media: `1_step_1_macOS.png` / `1_step_1.0_Windows.png`)
* **Carousel Item 2:** Check Python version and download the correct Google Cloud CLI installer. (Media: `1_step_2_macOS.png` / `1_step_2.0_Windows.png`)
* **Carousel Item 3:** Run the installer or drag 'install.sh' into the macOS Terminal. (Media: `1_step_3_macOS.png` / `1_step_3.0_Windows.png`)
* **Carousel Item 4:** Run 'gcloud init' in your terminal and log into your Google Account in the browser. (Media: `1_step_4_macOS.png` / `1_step_4.0_Windows.png`)
* **Chatbot Note:** Emphasize that choosing "Sign in with a new Google Account" is safer for passkey login.

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
