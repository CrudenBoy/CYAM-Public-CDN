**\# Updated Sections of teh Google Workspace CLI SPC file**

**Please incorporate the section of the \*\*Text for the [SPEC.md](http://SPEC.md) file for the \*\*Developer CLI Setup\*\* Level 2 Workflow\*\* verbatim into the [SPEC.md](http://SPEC.md) file, which is for Level 1: Category Sdmin Console for Task 2 and 3\. Task 1 will be in the [SPEC.md](http://SPEC.md) file will not be changed**

**\#\# Key Instructions**

**\*\*I have\*\* created a file called GWS\_Installation\_SKILL.md so you can use it as the [SKILL.md](http://SKILL.md) file**

**\*\*You will\*\*:** 

- **Tell me if the following case is not the protocol for this workflow based on the [SKILL.md](http://SKILL.md) for the dashboard\_v2.**  
- **Upload the new [SKILL.md](http://SKILL.md) file for the \*\*Developer CLI Setup\*\* Level 2 Workflow**  
- **Save the \`SKILL.md\` file in \`.agents/skills/gws-cli/\` in the CYAM-Platform workspace**  
- **Sync files for this workflow to the CDN GitHub repo where the other assets are saved to**  
- **Consider how we need to manage this in the instructions very carefully.**  
- **Changes ae required in Task 1 introduction, and Task 2 to 6 as follows in the SPEC**

**\#\# \*\*Revised AntiGravity Agent Prompt\*\***

**You will need to revise the AntiGravity Agent Prompt in Task 2 that references the [SPEC.md](http://SPEC.md) file** 

\>"Please refer to the SKILL.md save to GitHub CDN repo at xxxx and assist me with the Google Workspace CLI setup (Tasks 2 to 5). Start by verifying the installation of Node.js and then proceed to install the CLI. Guide me through the Google Cloud Console steps by providing the exact URLs, and then resume the technical configuration once I have my Client ID and Secret."

**\#\# Text for the [SPEC.md](http://SPEC.md) file for the \*\*Developer CLI Setup**

**Incorporate the following almost verbatim into the relevant sections of the [SPEC.md](http://SPEC.md) file**

**\#\#\# Task 1: Add Prerequisites below the heading of Task 1**

**\*\*Prerequisites\*\*** 

\- Node.js installed (verified via \`node \-v\`).

\- **\*\*Google Cloud CLI (gcloud)\*\*** installed and authenticated.

\- Access to a Google Workspace account.

**\#\#\# Task 2: Install Google Workspace CLI**

**\#\#\#\# AntiGravity Agent Prompt**

If you prefer to have an AI agent perform the technical parts of this setup, you can use the prompt below. AntiGravity will use the existing \`SKILL.md\` to guide you through Tasks 2 to 6, stopping only when your manual input (like choosing a Google account) is required.

**\*\*Recommended Prompt:\*\***

**\[GEMINI, INSERT \*\*Revised AntiGravity Agent Prompt\*\* here\]**

\---

**\#\#\#\# Step 1: Open Your Terminal**

Launch your system's command-line interface.

\> \[\!IMPORTANT\]

\> **\*\*Windows (PowerShell/CMD):\*\***

\> Search for 'PowerShell' in the Start menu. Right-click it and select **\*\*"Run as Administrator"\*\***.

\>

\> **\*\*macOS (Terminal):\*\***

\> Press **\*\*Cmd \+ Space\*\***, type 'Terminal', and press Enter.

**\#\#\#\# Step 2: Install the Package**

Run the following command exactly:

\`\`\`powershell

npm install \-g @googleworkspace/cli

\`\`\`

**\#\#\#\# Step 3: Verify Installation**

Wait for the process to finish, then verify by typing:

\`\`\`powershell

gws \--version

\`\`\`

\---

**\#\#\# Task 3: Google Cloud Console Setup (Manual Task)**

\> \[\!NOTE\]

\> This task must be performed by a human in a web browser because it involves security settings and 2FA.

**\#\#\#\# Step 1: Open/Create Your Project**

1\. Go to the \[Google Cloud Console\](https://console.cloud.google.com/).

2\. Click the **\*\*Project Dropdown\*\*** at the top left.

3\. Select an existing project (e.g., \`cyam-workspace-cli\`) or click **\*\*New Project\*\*** to create one.

**\#\#\#\# Step 2: Enable APIs and Services**

1\. Use the search bar at the top to find and **\*\*Enable\*\*** each of these APIs:

   \- **\*\*Gmail API\*\*** (Essential for email-to-sheet workflows)

   \- **\*\*Google Sheets API\*\*** (Essential for creating/editing spreadsheets)

   \- **\*\*Google Drive API\*\*** (Core requirement for most GWS tasks)

   \- **\*\*Google Calendar API\*\*** (Optional)

   \- **\*\*Google Docs API\*\*** (Optional)

**\#\#\#\# Step 3: Configure OAuth Consent Screen**

1\. Search for **\*\*"OAuth consent screen"\*\*** in the top search bar.

- \*\* Find OAuth Consent Screen\*\*  
- \*\* Click Get Started\*\*

2\. \*\* Add App Information\*\*

Click **\*\*Create\*\***.

4\. Fill in the **\*\*App Information\*\***:

   \- **\*\*App name\*\***: "GWS CLI"

   \- **\*\*User support email\*\***: Your email address.

3\. Select Audience: 

Select \*\*Internal\*\* (if you have a Workspace organization) or \*\*External\*\* (if using a personal @gmail.com account).

- 

4\. Add Contact Information

   \- **\*\*Developer contact info\*\***: Your email address.

5\. Click **\*\*Finish \*\*** through the remaining screens.

   You will be taken to Step 4 to **\*\*OAuth client ID\*\***.

**\#\#\#\# Step 4: Create Desktop Credentials**

1\. After completing Step 3, you will be asked to be taken to **\*\*Application type\*\*** screen. Alternatively, search for **\*\*"Credentials"\*\*** in the top search bar.

2\. Click **\*\*+ Create Credentials\*\*** \> **\*\*OAuth client ID\*\***.

3\. **\*\*Application type\*\***: Select **\*\*Desktop app\*\***.

4\. **\*\*Name\*\***: example "GWS CLI Desktop".

5\. Click **\*\*Create\*\***.

6\. **\*\*Save these\!\*\*** Copy the **\*\*Client ID\*\*** and **\*\*Client Secret\*\*** to a safe place; you will need them for the next task.

\---

**\#\#\# Task 4: CLI Authorization Setup**

**\#\#\#\# Step 1: Start CLI Setup**

In your terminal, run:

\`\`\`powershell

gws auth setup \--project your\-project\-id

\`\`\`

*\*(Replace* \`your-project-id\` *with the ID of the project you created/selected in Task 3).\**

**\#\#\#\# Step 2: Input Credentials**

When prompted, paste the **\*\*Client ID\*\*** and **\*\*Client Secret\*\*** you saved from Task 3\.

\---

**\#\#\# Task 5: Complete OAuth Login & Scopes**

**\#\#\#\# Step 1: Run Login Command**

Run the following command to grant the CLI access to your data:

\`\`\`powershell

gws auth login \-s drive,gmail,sheets

\`\`\`

**\#\#\#\# Step 2: Select Scopes in Terminal**

Use the arrow keys and **\*\*Space\*\*** to ensure these are checked:

\- \[x\] **\*\*Recommended (Core Consumer Scopes)\*\***

\- \[x\] **\*\*gmail.readonly\*\***

\- \[x\] **\*\*spreadsheets\*\***

Press **\*\*Enter\*\***.

**\#\#\#\# Step 3: Approve in Browser**

1\. A browser window will open. Select your Google account.

2\. **\*\*CRITICAL:\*\*** You must **\*\*manually check the boxes\*\*** for Gmail, Sheets, and Drive on the "GWS CLI wants to access your account" screen.

3\. Click **\*\*Allow\*\***.

\---

**\#\#\# Task 6: Verification**

**\#\#\#\# Step 1: Test Drive Access**

\`\`\`powershell

gws drive files list \--params '{"pageSize": 5}'

\`\`\`

**\#\#\#\# Step 2: Test Gmail/Sheets Integration**

Run a test to ensure the CLI can read emails and write to a sheet.

*\*(If you have a script for this, run it now, otherwise manually verify you can see your file list).\**

\---

**\#\# Level 4 Help & Context**

**\#\#\# Task 2: Installation Nuances**

The installation requires global permissions because \`npm\` writes to protected system folders. On Windows, if you see \`EPERM\` errors, it’s almost always because the terminal wasn't opened as Administrator. On macOS, prepending the command with \`sudo\` is the standard fix.

**\#\#\# Task 3: Why This is Manual**

Google Cloud Platform enforces strict security. Enabling APIs is like "unlocking doors" for the CLI tool. If you skip enabling the Gmail API, for example, the CLI will be "Authorized" to talk to your account but "Forbidden" from actually reading emails.

**\#\#\# Resources**

\- \[Official GWS CLI Documentation\](https://googleworkspace-cli.mintlify.app/)

\- \[Google Cloud Console\](https://console.cloud.google.com/)

\- \[Gmail API Scopes Reference\](https://developers.google.com/gmail/api/auth/scopes)

\---

**\#\# Text for Context\_knowledge.md file**

**\#\#\# Overview: GWS CLI Technical Architecture**

The \`gws\` CLI is a cross-platform tool that communicates with Google Workspace APIs via OAuth 2.0. It requires a Desktop-type OAuth Client ID associated with a GCP project where the relevant APIs (Drive, Gmail, Sheets) are enabled.

**\#\#\# Implementation Details**

\- **\*\*Configuration Storage\*\***: Settings are stored in \`$HOME/.config/gws/\`.

\- **\*\*Token Management\*\***: OAuth tokens are encrypted and cached in \`token\_cache.json\`.

\- **\*\*Scope Requirements\*\***: Core tasks require \`https://www.googleapis.com/auth/drive\`, \`https://www.googleapis.com/auth/gmail.readonly\`, and \`https://www.googleapis.com/auth/spreadsheets\`.

**\#\#\# Edge Cases & Troubleshooting**

| Issue | Likely Cause | Resolution |

| :--- | :--- | :--- |

| \`403 Forbidden\` | API not enabled in GCP | Go to Library and enable the specific API. |

| \`insufficientPermissions\` | Scopes not checked in browser | Re-run \`gws auth login\` and check all boxes. |

| \`Connection Refused\` | CLI listener timeout | Restart the login command and refresh browser. |

| \`EPERM\` (Windows) | Missing Admin rights | Restart terminal as "Run as Administrator". |

**\#\#\# Q\&A**

**\*\*Q: Can I use the same Client ID for multiple users?\*\***

A: Yes, the Client ID identifies the *\*application\** (the CLI), while the login process identifies the *\*user\**.

**\*\*Q: How do I change the project after setup?\*\***

A: Run \`gws auth setup \--project new-project-id\` to overwrite the existing configuration.

### **Key Links**

* **Official Docs:** [https://googleworkspace-cli.mintlify.app/](https://googleworkspace-cli.mintlify.app/)  
* **GitHub Repository:** [https://github.com/googleworkspace/cli](https://github.com/googleworkspace/cli)  
* **NPM Package:** [https://www.npmjs.com/package/@googleworkspace/cli](https://www.npmjs.com/package/@googleworkspace/cli)  
* **Video Tutorial (Fru Dev):** [https://www.youtube.com/watch?v=aci6mSkFPf8](https://www.youtube.com/watch?v=aci6mSkFPf8)