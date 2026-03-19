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

#### Level 4: Steps

1. Your computer must have **Node.js** installed to download the Workspace CLI. Node.js is an underlying software platform. If you do not have it, download and install it from the [official Node.js website](https://nodejs.org/).

> **🤖 Agent Automation**:
> "Please install Node.js and the latest version of Python 3 for me."

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

* **Carousel Item 1:** Download and install Node.js (required prerequisite).
  (Media: `install_nodejs.png`)
* **Carousel Item 2:** Check Python version and download the correct Google Cloud CLI installer.
  (Media: `install_gcloud_cli_download.png`)
* **Carousel Item 3:** Run the installer or drag 'install.sh' into the macOS Terminal.
  (Media: `install_gcloud_cli_run.png`)
* **Carousel Item 4:** Run 'gcloud init' in your terminal and log into your Google Account in the browser.
  (Media: `gcloud_init.png`)
* **Chatbot Note:** Emphasize that choosing "Sign in with a new Google Account" is safer for passkey login.

---

### Level 3: Task 2 — Install Google Workspace CLI

#### Level 4: Steps
1. Open your Terminal (macOS) or Command Prompt (Windows). *Windows users: search for 'cmd' in the Start menu, right-click it, and select "Run as Administrator".*
2. Run the following command exactly: `npm install -g @googleworkspace/cli`
3. Wait for the installation to complete.

##### Level 5: Help & Context

**Step 1 — Open Terminal:** On macOS, press `Cmd + Space`, type "Terminal", and press Enter. On Windows, search for "PowerShell" in the Start menu, **right-click** it and select **"Run as administrator"**. Administrator privileges are required because global npm installations write to protected system directories.

**Step 2 — npm install:** This command downloads and installs the Google Workspace CLI globally. The `-g` flag means it's available system-wide. On macOS, do **not** use `sudo`. Wait for it to say "added X packages" — this confirms success.

**Step 3 — Verify:** After installation completes, type `gws --version` to confirm. If you see "command not found", **close and reopen your terminal** (the PATH needs to refresh).

* **Carousel Item 1:** Run the npm install command in your terminal to get the Workspace CLI.
  (Media: `install_gws_cli.png`)

---

### Level 3: Task 3 — Google Cloud Console Setup (Select Project & Enable APIs)

#### Level 4: Steps
1. **Select Your Project**: 
   * Go to the [Google Cloud Console](https://console.cloud.google.com/).
   * Click the **Project Dropdown** at the top left of the screen (next to the Google Cloud logo).
   * Find and click on the `cyam-workspace-cli` project you just created in the terminal. Ensure it is showing at the top of the screen.
2. Open the left navigation menu (the three horizontal lines), and go to **APIs & Services > Library**.
3. **Enable APIs one by one**:
   * Use the "Search for APIs and services" search bar at the top of the Library page.
   * Type **Google Sheets API** and hit Enter.
   * Click on the "Google Sheets API" card in the search results.
   * Click the blue **Enable** button on the next page. Wait for the page to load showing it is enabled.
   * Go back to the **Library** page and repeat this exact search-and-enable process for the remaining four APIs: **Google Drive API**, **Gmail API**, **Google Calendar API**, and **Google Docs API**.

##### Level 5: Help & Context

**Step 1 — Select Project:** Open [Google Cloud Console](https://console.cloud.google.com/) in your browser. Click the **Project Dropdown** at the top-left (next to the Google Cloud logo). Search for and select `cyam-workspace-cli`. The project name should now appear in the top navigation bar.

**Step 2 — API Library:** Open the navigation menu (☰), go to **APIs & Services > Library**. This is the catalogue of all available Google APIs. Do not go to "Dashboard" — that shows already-enabled APIs.

**Step 3 — Enable APIs:** Search for each API by name, click the result card, then click the blue **Enable** button. Wait for each to load before returning to the Library for the next one. You need all five: **Google Sheets API, Google Drive API, Gmail API, Google Calendar API, Google Docs API**.

* **Carousel Item 1:** Click the Project Dropdown and select or create 'CYAM-Workspace-CLI'.
  (Media: `step6_create_new_project.png`)
* **Carousel Item 2:** Use the search bar in the Library to find and enable each API one by one.
  (Media: `step7_enable_apis.png`)

---

### Level 3: Task 4 — Configure OAuth Credentials

#### Level 4: Steps

1. In the left menu, go to **APIs & Services > OAuth consent screen**.
2. **First-Time Setup**: If you see a screen with a cloud icon saying "Google auth platform not configured yet", click the blue **Get started** button. 
3. On the next screen, provide the App Name (**CYAM-Workspace-CLI**) and your email in the support/developer contact fields, then click **Save and Continue** through the subsequent steps (scopes, etc.) to finish the initial setup.
4. Once completed, look at the left menu and click on the **Audience** tab.
5. Under "User type", look for **External** and click the **Make external** button.
6. A popup will ask for the "publishing status". Select **Testing** (do not select In production for this local tool) and click **Confirm**.
7. **WARNING - TEST USERS**: Scroll down the Audience tab to the "Test users" section. You MUST click **Add users** and enter your own Google account email address. Click Save. If you skip this, your login will be blocked later with an "Access blocked" error.
8. Go to **APIs & Services > Credentials** in the left menu.
9. Click **Create Credentials** at the top of the screen, and select **OAuth client ID**.
10. Select **Desktop app** as the application type, give it a name like "CLI Tool", and click **Create**.
11. Click **Download JSON** on the newly created credential. It will download to your `Downloads` folder as a file starting with `client_secret_` and ending with `.json`.
12. **Configure Hidden Directories Automatically:**

> **🤖 Agent Automation**:
> "I have downloaded the client_secret JSON file. Please find the most recent one in my Downloads folder, create the hidden ~/.config/gws/ directory if it doesn't exist, and move/rename the file there."

If you are doing this manually, do not manually look for the `.config` folder. Simply copy and paste the exact command for your operating system into your Terminal or PowerShell to automatically move the downloaded file to the correct hidden location:

[OS:macOS]
   * **macOS (Terminal):**
     Run: `mkdir -p ~/.config/gws && mv ~/Downloads/client_secret*.json ~/.config/gws/client_secret.json`
[/OS:macOS]

[OS:Windows]
   * **Windows (PowerShell):**
     Run: `New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.config\gws"; Move-Item -Path "$env:USERPROFILE\Downloads\client_secret*.json" -Destination "$env:USERPROFILE\.config\gws\client_secret.json"`
[/OS:Windows]

##### Level 5: Help & Context

**Steps 1-3 — OAuth Setup:** Navigate to **APIs & Services > OAuth consent screen**. Click "Get started" if this is a new project. Set the app name to exactly **CYAM-Workspace-CLI** and enter your email in both contact fields. Click Save and Continue through each screen.

**Steps 4-6 — Audience Config:** Click the **Audience** tab. Set user type to **External** and publishing status to **Testing**. Never select "In production" — that requires weeks of Google verification.

**Step 7 — CRITICAL Test Users:** Scroll to "Test users" and click **Add users**. Enter your exact Google email address. **This is the #1 cause of errors** — skipping this causes "Access blocked: This app's request is invalid" later.

**Steps 8-10 — Create Credentials:** Go to **Credentials > Create Credentials > OAuth client ID**. Select **Desktop app**. Click Create, then **Download JSON** from the success popup.

**Steps 11-12 — Save Credentials:** The JSON file must be saved to a specific hidden folder. On macOS: `mkdir -p ~/.config/gws && mv ~/Downloads/client_secret*.json ~/.config/gws/client_secret.json`. On Windows, use the PowerShell command or ask your AntiGravity Agent to do it for you.

* **Carousel Item 1:** Click 'Get started' on the OAuth screen, name the app 'CYAM-Workspace-CLI', and save.
  (Media: `oauth_get_started.png`)
* **Carousel Item 2:** On the Audience tab, click 'Make external', select 'Testing', and add your email to 'Test users'.
  (Media: `oauth_audience.png`)
* **Carousel Item 3:** Create a Desktop OAuth client and download the JSON file.
  (Media: `step8_desktop_app.png`)
* **Carousel Item 4:** Save the JSON file to the required hidden .config folder.
  (Media: `step9_save_client_secret.png`)
* **Chatbot Note:** Emphasize that they MUST add themselves as a 'Test user' in the OAuth consent screen. Explain that they shouldn't worry about being unverified since they own the app.

---

### Level 3: Task 5 — Verify Workspace CLI Connection

#### Level 4: Steps

1. Open your terminal or PowerShell.
2. Run the following command exactly: 
   `gws auth login --services drive,gmail,sheets`

> **🤖 Agent Automation**:
> "Please run the Workspace CLI auth login command with the drive, gmail, and sheets services."

3. **If your browser opens automatically**: 
   * Follow the prompts on the screen to log in to your Google Account and grant the requested permissions.
4. **If your browser DOES NOT open automatically**:
   * The terminal will output a very long web link starting with `https://accounts.google.com/...`
   * Carefully copy the ENTIRE URL. Make sure you do not miss any part of it, especially the end (it should end with `consent`). 
   * Paste the full URL into your web browser, hit Enter, and complete the sign-in process.
5. Once the web page says the authentication was successful, you can close the tab. The `gws` command running in the background of your terminal will automatically detect it and finish!
6. To confirm everything is securely connected to your primary application (Google Drive), run this specific verification command:
   `gws drive files list --params '{"pageSize": 5}'`

> **🤖 Agent Automation**:
> "Please run the verification command to list the 5 most recent files in my Google Drive to confirm the Workspace CLI is connected correctly."

7. If the terminal prints out names of your recent Google Drive files, your installation is fully verified and successful!

##### Level 5: Help & Context

**Steps 1-2 — Auth Login:** Open a terminal and run `gws auth login --services drive,gmail,sheets`. The `--services` flag limits access to only what CYAM needs. On Windows, if you see "execution of scripts is disabled", run `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` first.

**Steps 3-4 — Browser Flow:** Your browser should open automatically. If it doesn't, look for a long URL in the terminal starting with `https://accounts.google.com/...` — copy the **entire** URL and paste it into your browser. Log in and click "Allow".

**Step 5 — Safety Warning:** You may see "Google hasn't verified this app" — this is expected. Click **Advanced** then **Go to CYAM-Workspace-CLI (unsafe)**. It's safe because you created this app yourself.

**Steps 6-7 — Verify:** Run `gws drive files list --params '{"pageSize": 5}'` to list your 5 most recent Drive files. On Windows PowerShell, you may need to use escaped quotes: `--params "{\`"pageSize\`": 5}"`. If files appear, your setup is complete!

* **Carousel Item 1:** Run 'gws auth login' with limited scopes and approve the consent screen.
  (Media: `gws_auth_login.png`)
* **Carousel Item 2:** Test your setup by listing your Google Drive files in the terminal.
  (Media: `gws_drive_verify.png`)
* **Chatbot Note:** Remind them that 'gws auth login' might fail if they don't limit the scopes for an unverified app.

---

## Context & Chatbot Delivery Summary

| Field | Value |
|---|---|
| `INSTALL_CHATBOT` | `true` |
| `chatbot_context_file` | `GoogleWorkspaceCLI_Context_Knowledge.md` |
| Context URLs | Listed in `metadata.json` |
