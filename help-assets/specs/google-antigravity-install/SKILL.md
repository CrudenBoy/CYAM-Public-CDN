---  
name: Google Workspace CLI Setup  
description: Guide for installing, configuring, and verifying the @googleworkspace/cli (GWS CLI) for non-technical users.  
---

# Google Workspace CLI (GWS) Setup Guide

This skill provides a step-by-step walkthrough for setting up the Google Workspace CLI, including the manual steps required in the Google Cloud Console.

## Prerequisites  
- Node.js installed (verified via `node -v`).  
- Access to a Google Workspace account (e.g., `user@your-org.com`).

---

## Step 1: Installation  
Open your terminal (PowerShell or Command Prompt) and run:  
```powershell  
npm install -g @googleworkspace/cli  
```

---

## Step 2: Initialize Configuration  
Run the setup wizard to link the CLI to a Google Cloud project:  
```powershell  
gws auth setup  
```  
> [!TIP]  
> If you already have a Project ID, you can skip the selection menu by running:  
> `gws auth setup --project your-project-id`

### Step 2: Enable Required APIs  
1. Use the search bar at the top to find and **Enable** each of these APIs:  
   - **Gmail API** (Essential for email-to-sheet workflows)  
   - **Google Sheets API** (Essential for creating/editing spreadsheets)  
   - **Google Drive API** (Core requirement)  
   - **Google Calendar API** (Optional)  
   - **Google Docs API** (Optional)

### Step 3: Manual OAuth Configuration (Google Cloud Console)  
When the CLI asks for an **OAuth Client ID**, you must manually configure it in the [Google Cloud Console](https://console.cloud.google.com/).

### 3.1 Configure OAuth Consent Screen  
1. Search for "OAuth consent screen" in the top search bar.  
2. **User Type**: Select **Internal** (if available for your org) and click **Create**.  
3. **App Information**:  
   - **App name**: Enter "GWS CLI".  
   - **User support email**: Select your email.  
   - **Developer contact info**: Enter your email.  
4. Click **Save and Continue** until you reach the dashboard.

### 3.2 Create OAuth Client ID  
1. Search for "Credentials" in the top search bar.  
2. Click **+ Create Credentials** at the top and select **OAuth client ID**.  
3. **Application type**: Select **Desktop app**.  
4. **Name**: Enter any name (e.g., "GWS CLI Desktop").  
5. Click **Create**.

### 3.3 Capture Credentials  
A dialog will appear with your **Client ID** and **Client Secret**.  
1. **Copy the Client ID** and paste it into the waiting terminal.  
2. **Copy the Client Secret** and paste it when prompted.

---

## Step 4: OAuth Login & Scopes  
Once setup is complete, run the login command:  
```powershell  
gws auth login -s drive,gmail,sheets  
```

### 4.1 CLI Scope Selection  
A list will appear in your terminal. Use the arrow keys and **Space** to toggle:  
- [x] `✨ Recommended (Core Consumer Scopes)`  
- [x] `gmail.readonly` - (To view emails)  
- [x] `spreadsheets` - (To manage Google Sheets)  
- [x] `drive` or `drive.file` - (To manage Drive files)  
Press **Enter** to confirm.

### 4.2 Browser Handshake  
1. A URL will appear; open it in your browser.  
2. Select your workspace account.  
3. **Check ALL the boxes** for the permissions requested (Gmail, Drive, Sheets).  
4. Click **Allow** at the bottom.

---

## Step 5: Verification Tests

### 5.1 Simple Drive List  
```powershell  
gws drive files list --params '{"pageSize": 5}'  
```

### 5.2 Email-to-Sheet Export  
To test more complex integration, you can use a script to export recent email subjects to a new Google Sheet:  
1. Fetch the last 10 Gmail messages.  
2. Create a new Sheet:  
   ```powershell  
   gws sheets spreadsheets create --params '{"properties": {"title": "Recent Emails Overview"}}'  
   ```  
3. Append the data using `gws sheets +append`.

---

## Troubleshooting  
- **Connection Refused on Localhost**: If the browser fails to connect to `localhost`, ensure your terminal is still running the login command. If it times out, restart the `gws auth login` command.  
- **Insufficient Permissions**: If you get a 403 error, your token might be missing scopes. Run `gws auth login -s drive,gmail,sheets` again and ensure every checkbox is checked in the browser.  
- **Cache Clearing**: If you getting stuck with old permissions, clear the cache manually:  
  ```powershell  
  Remove-Item -Path "$HOME\.config\gws\token_cache.json" -Force  
  ```

---  
## References  
- [Google Workspace CLI GitHub Repository](https://github.com/googleworkspace/cli)  
- [Gmail API Documentation](https://developers.google.com/gmail/api/reference/rest)  
- [Sheets API Documentation](https://developers.google.com/sheets/api/reference/rest)
