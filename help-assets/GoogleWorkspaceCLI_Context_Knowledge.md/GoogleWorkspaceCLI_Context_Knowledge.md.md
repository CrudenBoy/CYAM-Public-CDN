# GoogleWorkspaceCLI_Context_Knowledge.md  
  
## 1. Core Workflow Definitions  
**What This Workflow Achieves:**  
This comprehensive workflow establishes a secure, authenticated connection between a user’s local computer and Google’s cloud infrastructure, specifically enabling the CYAM Platform’s AI agents to programmatically interact with Google Workspace applications. By completing this setup, users authorize CYAM’s automation capabilities to read, create, modify, and manage files and communications within Google Drive, Gmail, Google Sheets, Google Calendar, and Google Docs without requiring manual intervention for each action.  
**The Technical Foundation:**  
**The Technical Foundation:**  
The workflow involves installing and configuring two distinct but interconnected command-line interfaces (CLIs):  
1. **Google Cloud CLI (gcloud)**: Provides the authentication infrastructure, project management, and API enablement capabilities that serve as the foundation for all Google Cloud interactions.  
2. **Google Workspace CLI (gws)**: A specialized tool that provides direct, programmatic access to Workspace services through simple command-line operations.  
**End State Success Criteria:**  
When this workflow completes successfully, the user will have:  
* Both CLIs installed and accessible from any terminal/command prompt window  
* A dedicated Google Cloud project (cyam-workspace-cli) configured for CYAM operations  
* Five critical Google Workspace APIs enabled (Sheets, Drive, Gmail, Calendar, Docs)  
* OAuth credentials properly configured with appropriate test user access  
* Authenticated sessions established for both CLIs  
* Verified ability to programmatically access Google Drive files from the command line  
**Security and Privacy Context:**  
This setup maintains user control and security by using OAuth 2.0 authentication, which means users grant specific, revocable permissions to the CYAM tools without sharing passwords. The OAuth consent screen configuration ensures only authorized users (test users) can access the application during development and testing phases.  
  
## 2. Step-by-Step Guidance Context  
## Task 1: Install Google Cloud CLI  
**Step 1: Install Node.js (Prerequisite)**  
**Purpose and Context:**  
**Purpose and Context:**  
Node.js is a JavaScript runtime environment required by the Google Workspace CLI (to be installed in Task 2). While not directly needed for Google Cloud CLI installation, ensuring Node.js is present now prevents workflow interruption later. Node.js includes npm (Node Package Manager), which is the installation mechanism for the Workspace CLI.  
**Verification Process:**  
**Verification Process:**  
* Open Terminal (macOS) or PowerShell (Windows)  
* Execute: node -v  
* Expected output: Version number like v18.19.0, v20.11.0, or v22.x.x  
**macOS Installation:**  
* Navigate to ++[https://nodejs.org/en/download](https://nodejs.org/en/download)++  
* Download the **LTS (Long Term Support)** .pkg installer  
* Double-click and follow installation prompts  
* Accept all default settings  
**Windows Installation (Detailed):**  
* Navigate to ++[https://nodejs.org/en/download](https://nodejs.org/en/download)++  
* Download the **LTS** .msi installer (64-bit for most modern systems)  
* Run the installer as Administrator (right-click → “Run as administrator”)  
* **CRITICAL**: On the installation options screen, ensure “Add to PATH” is checked (it’s enabled by default)  
* Accept all other default settings  
* Click “Install” and wait for completion  
**Post-Installation Verification:**  
* **Close and reopen** terminal/PowerShell to refresh environment variables  
* Re-verify with node -v and npm -v  
* Both should return version numbers  
**Common Pitfalls:**  
* Users sometimes download Current (latest) instead of LTS, which may have compatibility issues  
* Forgetting to open a fresh terminal after installation means PATH changes aren’t recognized  
* On Windows, not running installer as Administrator can cause permission issues  
  
**Step 2: Check Python Version**  
**Purpose and Context:**  
**Purpose and Context:**  
The Google Cloud CLI is built with Python and requires Python 3.8 or newer to function. This step verifies Python is installed and meets version requirements before proceeding with CLI installation.  
**macOS Instructions:**  
**macOS Instructions:**  
Command: python3 -V (uppercase V is required for version flag)  
Command: python3 -V (uppercase V is required for version flag)  
Expected output: Python 3.8.x or higher (3.9, 3.10, 3.11, 3.12 are all acceptable)  
Expected output: Python 3.8.x or higher (3.9, 3.10, 3.11, 3.12 are all acceptable)  
**Why python3 specifically on macOS**: macOS includes an outdated Python 2.7 installation at /usr/bin/python for system compatibility. Modern Python 3 installations use the python3 command to avoid conflicts.  
**Why python3 specifically on macOS**: macOS includes an outdated Python 2.7 installation at /usr/bin/python for system compatibility. Modern Python 3 installations use the python3 command to avoid conflicts.  
**If Python Is Not Found on macOS:**  
**If Python Is Not Found on macOS:**  
1. Visit ++[https://www.python.org/downloads/](https://www.python.org/downloads/)++  
2. Download the latest stable macOS installer (.pkg file)  
3. Run installer with default settings  
4. Verify installation with python3 -V  
**Windows Instructions (Comprehensive):**  
**Initial Check:**Command: python -V (uppercase V is required)Expected output: Python 3.8.x or higher  
**If Python Opens Microsoft Store:**This means Python isn’t properly installed. Windows is redirecting to the Store app installer.  
**Windows Python Installation (Detailed Steps):**  
1. Visit ++[https://www.python.org/downloads/](https://www.python.org/downloads/)++  
2. Click “Download Python 3.x.x” (latest stable version)  
3. **CRITICAL FIRST STEP**: On the very first installer screen, check the box labeled **“Add Python to PATH”**  
4. Click “Install Now” (recommended) or “Customize installation” for advanced users  
5. If using custom installation:  
    * Check “Add Python to environment variables”  
    * Check “Install for all users” if you have admin rights  
6. Wait for installation to complete  
7. Click “Close” when finished  
**Windows Post-Installation Verification:**  
```
# Close and reopen PowerShell first
python -V
pip -V

```
**Windows Troubleshooting:**  
* If python still opens Microsoft Store: Reinstall Python with “Add to PATH” checked  
* If python command not found: Add manually to PATH via System Properties → Environment Variables  
* Check installation location: Usually C:\Python3x\ or C:\Users\%USERNAME%\AppData\Local\Programs\Python\Python3x\  
**Common Pitfalls:**  
* Windows users forgetting to check “Add Python to PATH” during installation (most common issue)  
* macOS users typing python instead of python3  
* Users with very old Python installations (2.x) that need upgrading  
  
**Step 3: Download the Installer**  
**Purpose and Context:**  
**Purpose and Context:**  
This step acquires the authentic Google Cloud CLI installation package directly from Google’s official distribution servers. Using official sources ensures security, integrity, and compatibility.  
**Official Download Page**: ++[https://cloud.google.com/sdk/docs/install](https://cloud.google.com/sdk/docs/install)++  
**macOS Platform Selection:**  
Modern Macs use two different processor architectures:  
* **Apple Silicon (M1, M2, M3, M4 chips)**: Select the **ARM64 / macOS Apple Silicon** version  
* **Intel Processors**: Select the **x86_64 / macOS Intel** version  
**How to Check Your Mac’s Processor:**  
1. Click the Apple menu () in top-left corner  
2. Select “About This Mac”  
3. Look at the “Chip” or “Processor” line:  
    * If it says “Apple M1”, “Apple M2”, “Apple M3”, or “Apple M4” → Use ARM64 version  
    * If it says “Intel Core i5”, “Intel Core i7”, etc. → Use x86_64 version  
The download will be a .tar.gz archive file (compressed archive format).  
**Windows Platform Selection (Detailed):**  
**Windows Platform Selection (Detailed):**  
**Recommended Option**: Select the **Windows 64-bit bundled Python** installer (.exe file)  
* Filename typically: google-cloud-cli-XXX-windows-x86_64-bundled-python.exe  
* This includes Python and handles all dependencies automatically  
* Most modern Windows systems (Windows 10, Windows 11) are 64-bit  
**Alternative Option**: Standard Windows installer without bundled Python  
* Only choose this if you’re confident your Python installation is correct  
* Requires Python 3.8+ to be properly installed and accessible  
**Download Location**: Files typically download to your Downloads folder unless you’ve configured a different location.  
**Security Note**: Only download from ++[cloud.google.com](http://cloud.google.com/)++. Third-party mirrors or unofficial sources may contain modified or malicious versions.  
  
**Step 4: Extract the Download**  
**Purpose and Context:**  
Installation files are compressed for faster downloading. This step unpacks the installation files so they can be executed.  
**macOS Extraction Process:**  
**macOS Extraction Process:**  
1. Navigate to your Downloads folder in Finder  
2. Locate the file named something like google-cloud-cli-darwin-arm.tar.gz (ARM) or google-cloud-cli-darwin-x86_64.tar.gz (Intel)  
3. **Double-click the .tar.gz file**  
4. macOS automatically extracts it, creating a folder named google-cloud-sdk  
5. Verify the google-cloud-sdk folder contains an install.sh file (this is the installer script)  
**Alternative macOS Extraction (Terminal Method):**  
```
cd ~/Downloads
tar -xzf google-cloud-cli-*.tar.gz

```
**Windows Extraction Process (Comprehensive):**  
**For .exe Installer (Recommended):**  
1. Navigate to your Downloads folder in File Explorer  
2. Locate the file named something like google-cloud-cli-XXX-windows-x86_64-bundled-python.exe  
3. **Right-click the .exe file and select “Run as administrator”**  
4. If Windows Security shows a warning:  
    * “Windows protected your PC” → Click **“More info”**  
    * Then click **“Run anyway”**  
    * This is normal for new installers from external sources  
**Windows Installation Wizard Steps:**  
1. **Welcome Screen**: Click “Next”  
2. **License Agreement**: Read and click “I Agree”  
3. **Installation Type**:  
    * Choose “Install for all users” (requires admin) or “Install for current user only”  
    * Recommended: “Install for all users” if you have admin rights  
4. **Installation Location**:  
    * Default: C:\Program Files (x86)\Google\Cloud SDK\  
    * Accept default unless you have specific reasons to change  
5. **Component Selection**:  
    * **CRITICAL**: Ensure “Google Cloud CLI Core Libraries” is checked  
    * **CRITICAL**: Ensure “Bundled Python” is checked (if using bundled version)  
    * Leave other components as default  
6. **Installation Options**:  
    * **CRITICAL**: Check “Start Google Cloud CLI Shell”  
    * **CRITICAL**: Check “Run gcloud init”  
    * These options launch setup automatically after installation  
7. Click “Install” and wait for completion (typically 2-5 minutes)  
**Post-Installation (Windows):**  
* A “Google Cloud SDK Shell” window should open automatically  
* This is a specially configured Command Prompt with all paths set correctly  
* Keep this window open for the next step  
**Common Pitfalls:**  
* macOS users trying to open .tar.gz with wrong applications (double-click should work automatically)  
* Windows users not running installer as Administrator, causing permission issues  
* Windows users unchecking important installation options  
* Getting blocked by antivirus (temporarily disable if necessary, then re-enable)  
  
**Step 5: Run the Installer**  
**Purpose and Context:**  
**Purpose and Context:**  
This step executes the installation script/wizard that copies Google Cloud CLI files to the appropriate system locations and configures your system to recognize gcloud commands.  
**macOS Installation Process:**  
1. **Open Terminal Application:**  
    * Press Cmd + Space to open Spotlight  
    * Type “Terminal” and press Enter  
    * Or navigate to Applications > Utilities > Terminal  
2. **Execute the Installer:**  
    * In Finder, navigate to the google-cloud-sdk folder you extracted  
    * Locate the install.sh file  
    * **Drag and drop** the install.sh file directly into the Terminal window  
    * The Terminal will show the full path to the file  
    * Press **Enter** to execute  
3. **Interactive Prompts (Answer Carefully):****Prompt 1**: “Do you want to help improve the Google Cloud CLI (y/N)?”  
    * **Answer**: N (press N then Enter)  
    * This opts out of anonymous usage statistics  
4. **Prompt 2**: “Modify profile to update your $PATH and enable shell command completion?”  
    * **Answer**: Y (press Y then Enter)  
    * **CRITICAL**: This step adds gcloud to your system PATH, making it accessible from any terminal window  
    * Answering No here means gcloud commands won’t work without manual PATH configuration  
5. **Prompt 3**: “Enter a path to an rc file to update, or leave blank to use [default path]:”  
    * **Answer**: Press **Enter** (accept default)  
    * The installer auto-detects your shell (bash, zsh) and updates the correct configuration file  
6. **Prompt 4**: Password prompt (may appear if system modifications require elevated privileges)  
    * Type your macOS login password  
    * **Note**: Characters won’t appear as you type (security feature)  
    * Press Enter after typing password  
7. **Completion**: Installer will display “Google Cloud CLI has been installed” or similar confirmation message.  
**Windows Installation Process (Already Completed in Step 4):**  
If you followed Step 4 correctly, the Windows installation is already complete. The installer wizard handles everything automatically. You should now have:  
* **Google Cloud SDK Shell** window open (specially configured Command Prompt)  
* gcloud command available in regular PowerShell/Command Prompt  
* All necessary PATH variables set  
**Windows Verification:**  
1. **In the Google Cloud SDK Shell** (should be open):gcloud --version  
2. Expected: Version information display  
3. **In a new regular PowerShell window**:gcloud --version  
4. Expected: Same version information (confirms PATH is set correctly)  
**Windows Troubleshooting:**  
* If gcloud not found in regular PowerShell: Use “Google Cloud SDK Shell” from Start menu  
* If installation failed: Re-run installer as Administrator  
* If PATH issues persist: Manually add to PATH via System Properties → Environment Variables  
**Common Pitfalls:**  
* macOS users answering ‘N’ to PATH modification, then wondering why gcloud doesn’t work  
* Windows users not running installer as Administrator  
* Not opening a fresh terminal after installation (old terminals don’t have updated PATH)  
  
**Step 6: Log In and Initialize**  
**Purpose and Context:**  
This critical step authenticates your identity with Google Cloud, creates a dedicated project for CYAM operations, and configures the CLI with default settings. The gcloud init command is an interactive wizard that guides you through initial setup.  
This critical step authenticates your identity with Google Cloud, creates a dedicated project for CYAM operations, and configures the CLI with default settings. The gcloud init command is an interactive wizard that guides you through initial setup.  
**Prerequisites Before Starting:**  
**Prerequisites Before Starting:**  
* Installation must be complete  
* For macOS: Open a **brand new Terminal window** (to load updated PATH)  
* For Windows: Use the “Google Cloud SDK Shell” that opened after installation, or open a fresh PowerShell window  
**Initialization Process:**  
1. **Execute Initialization Command:**gcloud init  
2.   
3. **Interactive Prompts (Follow Carefully):****Prompt 1**: “Pick configuration to use:”[1] Re-initialize this configuration [default] with new settings  
4. [2] Create a new configuration  
5.   
    * **Answer**: Type 1 and press Enter  
    * This uses the default configuration profile  
6. **Prompt 2**: “Choose the account you would like to use to perform operations for this configuration:”[1] [existing-email@gmail.com] (if any existing accounts)  
7. [2] Log in with a new account  
8.   
    * **Answer**: Type 2 and press Enter (select “Log in with a new account”)  
    * **Why**: This ensures you use the browser-based OAuth flow, which supports modern authentication methods like passkeys and Face ID  
9. **Browser Authentication Flow:****Automatic Browser Opening (Preferred):**  
    * Your default web browser should open automatically to a Google sign-in page  
    * Sign in to your Google Account using your preferred method (password, passkey, Face ID, etc.)  
    * You’ll see a consent screen: “Google Cloud SDK wants to access your Google Account”  
    * **Click “Allow”**  
    * Browser will show “You are now authenticated with the gcloud CLI!”  
    * **Close the browser tab** and return to your terminal  
10. **Manual Browser Opening (If Automatic Fails):**  
    * If browser doesn’t open automatically, the terminal will display a URL  
    * Copy the entire URL starting with https://accounts.google.com/o/oauth2/...  
    * Paste it into your browser manually  
    * Complete the same authentication flow as above  
11. **Windows-Specific Browser Issues:**  
    * If using Windows and browser doesn’t open, check Windows Defender or antivirus settings  
    * Some corporate networks block automatic browser launching  
    * Always use the manual URL method as fallback  
12. **Back in Terminal - Project Selection:****Prompt 3**: “Pick cloud project to use:”[1] [existing-project-id] (if you have any existing projects)  
13. [2] Create a new project  
14.   
    * **Answer**: Type 2 and press Enter (Create a new project)  
15. **Prompt 4**: “Enter a Project ID, or leave blank to use a generated one:”  
    * **Answer**: Type cyam-workspace-cli and press Enter  
    * **CRITICAL**: Use exactly this project ID for consistency with CYAM documentation  
16. **If Project ID Is Unavailable:**  
    * Project IDs are globally unique across all Google Cloud users  
    * If someone else already used cyam-workspace-cli, you’ll see an error  
    * Try variations:  
        * cyam-workspace-cli-yourname (replace yourname with your actual name)  
        * cyam-workspace-cli-2026  
        * cyam-workspace-cli-v2  
    * **Document the final project ID you use** - you’ll need it for later configuration  
17. **Completion Confirmation:**  
    * Terminal displays: “Your current project has been set to: [cyam-workspace-cli]”  
    * Followed by: “The Google Cloud CLI is configured and ready to use!”  
**Verification:**  
```
gcloud config list

```
Expected output shows your account and project:  
```
[core]
account = your-email@gmail.com
project = cyam-workspace-cli

```
**Common Pitfalls:**  
* Using old terminal windows that don’t have updated PATH  
* Not completing browser authentication (leaving the browser tab open but not clicking Allow)  
* Skipping project creation and trying to proceed without a project  
* Forgetting which project ID variation was used if cyam-workspace-cli wasn’t available  
  
## Task 2: Install Google Workspace CLI  
**Step 1: Open Terminal (macOS) or Command Prompt as Administrator (Windows)**  
**Purpose and Context:**  
**Purpose and Context:**  
The Google Workspace CLI installation requires writing files to system-protected directories, which necessitates elevated privileges on Windows. On macOS, npm installations with the -g (global) flag typically don’t require sudo if Node.js was installed correctly, but the terminal must be properly configured.  
The Google Workspace CLI installation requires writing files to system-protected directories, which necessitates elevated privileges on Windows. On macOS, npm installations with the -g (global) flag typically don’t require sudo if Node.js was installed correctly, but the terminal must be properly configured.  
**macOS Instructions:**  
1. **Open Terminal:**  
    * Press Cmd + Space to open Spotlight Search  
    * Type “Terminal” and press Enter  
    * Or navigate to Applications > Utilities > Terminal  
2. **No Special Privileges Needed:**  
    * Regular Terminal window is sufficient  
    * Do NOT use sudo with npm commands (can cause permission issues)  
**Windows Instructions (Comprehensive):**  
**Method 1 - Start Menu (Recommended):**  
**Method 1 - Start Menu (Recommended):**  
1. Click Start button (Windows icon)  
2. Type “PowerShell” or “cmd”  
3. **Right-click** on “Windows PowerShell” or “Command Prompt” in results  
4. Select **“Run as administrator”**  
5. Click **“Yes”** on the User Account Control (UAC) prompt  
**Method 2 - Power User Menu:**  
1. Press Win + X keys together  
2. Select **“Windows PowerShell (Admin)”** or **“Command Prompt (Admin)”**  
3. Click **“Yes”** on the UAC prompt  
**Method 3 - Search and Keyboard Shortcut:**  
1. Press Win + S to open search  
2. Type “PowerShell”  
3. Press Ctrl + Shift + Enter (this keyboard shortcut runs as administrator)  
4. Click **“Yes”** on the UAC prompt  
**Method 4 - Windows Terminal (If Installed):**  
1. Press Win + X  
2. Select **“Windows Terminal (Admin)”**  
3. Click **“Yes”** on the UAC prompt  
4. Ensure you’re in a PowerShell tab (not Command Prompt)  
**Verify Administrator Mode:**  
* The window title should say **“Administrator: Windows PowerShell”** or **“Administrator: Command Prompt”**  
* The prompt should show C:\Windows\System32> or similar system path  
* You can also run whoami /groups and look for “BUILTIN\Administrators”  
**Why Administrator Rights Are Required on Windows:**  
Global npm packages (-g flag) install to protected system directories:  
Global npm packages (-g flag) install to protected system directories:  
* Typical location: C:\Program Files\nodejs\node_modules\  
* Or: C:\Users\%USERNAME%\AppData\Roaming\npm\  
Without administrator privileges, the installation will fail with “EACCES: permission denied” errors.  
**Windows Execution Policy Check:**Before installing, check if PowerShell execution policies will block npm scripts:  
```
Get-ExecutionPolicy -Scope CurrentUser

```
If it returns “Restricted” or “Undefined”, you may need to change it:  
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

```
Type Y when prompted.  
**Common Pitfalls:**  
* Windows users opening regular Command Prompt instead of Administrator version (most common issue)  
* macOS users unnecessarily using sudo with npm, which creates permission conflicts  
* Forgetting to verify administrator mode before proceeding  
* Windows users not addressing Execution Policy restrictions  
  
**Step 2: Run npm install -g @googleworkspace/cli**  
**Step 2: Run npm install -g @googleworkspace/cli**  
**Purpose and Context:**  
**Purpose and Context:**  
This command uses npm (Node Package Manager) to download and install the Google Workspace CLI package globally on your system. The -g flag means “global,” making the gws command available system-wide from any directory.  
This command uses npm (Node Package Manager) to download and install the Google Workspace CLI package globally on your system. The -g flag means “global,” making the gws command available system-wide from any directory.  
**Installation Command:**  
**Installation Command:**  
```
npm install -g @googleworkspace/cli

```
**What Happens During Installation:**  
1. **Package Download:**  
    * npm connects to the official npm registry (++[npmjs.com](http://npmjs.com/)++)  
    * Downloads the @googleworkspace/cli package and all its dependencies  
    * Typical download size: 10-30 MB depending on dependencies  
2. **Installation Process:**  
    * Extracts package files  
    * Creates executable scripts  
    * Adds gws command to system PATH  
    * Configures necessary symlinks  
3. **Console Output:**  
    * You’ll see multiple lines showing download progress  
    * Dependency tree being built  
    * Installation location confirmation  
**Expected Output (Successful Installation):**  
```
npm WARN deprecated some-package@1.0.0: This package is deprecated
added 45 packages in 12s

5 packages are looking for funding
  run `npm fund` for details

```
**Installation Location:**  
* **macOS**: /usr/local/lib/node_modules/@googleworkspace/cli or /opt/homebrew/lib/node_modules/@googleworkspace/cli  
* **Windows**: C:\Program Files\nodejs\node_modules\@googleworkspace\cli or C:\Users\%USERNAME%\AppData\Roaming\npm\node_modules\@googleworkspace\cli  
**Windows-Specific Installation Monitoring:**  
```
# Monitor installation progress (in another PowerShell window)
Get-Process npm -ErrorAction SilentlyContinue

# Check global packages after installation
npm list -g --depth=0

```
**Windows Installation Troubleshooting:**  
**Issue: Installation Hangs**  
* Press Enter once - sometimes Windows console pauses output  
* Check Task Manager for npm process  
* Ensure internet connectivity: Test-NetConnection npmjs.com -Port 443  
**Issue: Network/Proxy Errors**  
```
# Configure npm for corporate proxy (if applicable)
npm config set proxy http://proxy.company.com:8080
npm config set https-proxy http://proxy.company.com:8080

# Retry installation
npm install -g @googleworkspace/cli

```
**Issue: Cache Problems**  
```
# Clear npm cache and retry
npm cache clean --force
npm install -g @googleworkspace/cli

```
**Common Pitfalls:**  
* Running without administrator privileges on Windows (causes EACCES errors)  
* Network connectivity issues preventing package download  
* npm: command not found (indicates Node.js wasn’t installed or PATH not updated)  
* Corporate proxies blocking npm from accessing the internet  
* Outdated npm version causing compatibility issues (update with npm install -g npm)  
**Platform Notes:**  
**macOS Specific:**  
**macOS Specific:**  
* If you see permission errors writing to /usr/local/lib, your Node.js installation may have permission issues  
* Avoid using sudo npm install -g as it can cause ownership problems  
* Consider using Node Version Manager (nvm) for better permission handling  
**Windows Specific:**  
* Admin Command Prompt or Admin PowerShell is strongly recommended  
* If you installed Node only for a specific user, ensure you’re using the same user account  
* Windows Defender may scan downloaded packages, causing temporary delays  
  
**Step 3: Wait for Installation to Complete**  
**Purpose and Context:**  
npm installations can take 30 seconds to several minutes depending on network speed and system performance. This step emphasizes patience and provides guidance on recognizing successful completion versus errors.  
**What to Watch For:**  
**What to Watch For:**  
**Success Indicators:**  
**Success Indicators:**  
* Final line shows added X packages in Ys (e.g., “added 45 packages in 12s”)  
* No error messages or red text  
* Command prompt returns (cursor blinks, ready for next command)  
**Progress Indicators (Normal):**  
* Lines showing package names being downloaded  
* Progress bars or spinners  
* “npm WARN” messages (warnings are usually not critical)  
**Error Indicators (Require Action):**  
* Red text with “npm ERR!” prefix  
* “EACCES: permission denied” (Windows: need administrator; macOS: don’t use sudo)  
* “ENOTFOUND” or “ETIMEDOUT” (network connectivity issues)  
* “404 Not Found” (package name typo or package doesn’t exist)  
**Verification After Installation:**  
**Basic Verification:**  
**Basic Verification:**  
```
gws --version
gws --help

```
Expected output: Version number like 1.0.0 or similar, followed by help text  
**Windows-Specific Verification:**  
**Windows-Specific Verification:**  
```
# Check if gws is in PATH
where.exe gws

# Verify global npm packages
npm list -g --depth=0 | Select-String "@googleworkspace/cli"

# Test command accessibility
gws --version

```
**macOS-Specific Verification:**  
```
# Check if gws is in PATH
which gws

# Verify global npm packages
npm list -g --depth=0 | grep "@googleworkspace/cli"

# Test command accessibility
gws --version

```
**If gws Command Not Found:**  
**Immediate Steps:**  
**Immediate Steps:**  
1. Close and reopen terminal/command prompt (PATH needs to refresh)  
2. Verify Node.js and npm are properly installed: npm -v  
3. Check global npm installation directory: npm config get prefix  
**Windows Advanced Troubleshooting:**  
```
# Check npm global installation path
npm config get prefix

# Verify PATH includes npm global bin directory
$env:PATH -split ';' | Select-String "npm"

# Manual PATH addition if needed (temporary)
$env:PATH += ";$(npm config get prefix)"

# Test gws again
gws --version

```
**macOS Advanced Troubleshooting:**  
```
# Check npm global installation path
npm config get prefix

# Verify PATH includes npm global bin directory
echo $PATH | grep -o '[^:]*npm[^:]*'

# Manual PATH addition if needed (temporary)
export PATH="$(npm config get prefix)/bin:$PATH"

# Test gws again
gws --version

```
**Common Pitfalls:**  
* Interrupting installation mid-process (Ctrl+C) leaves partial installation  
* Not waiting for command prompt to return before proceeding  
* Assuming installation failed when seeing warning messages (warnings ≠ errors)  
* Not refreshing terminal session after installation  
  
## Task 3: Google Cloud Console Setup — Select Project & Enable APIs  
**Step 1: Select cyam-workspace-cli Project in Google Cloud Console**  
**Purpose and Context:**  
The Google Cloud Console is the web-based interface for managing Google Cloud resources. Before enabling APIs, you must ensure you’re working within the correct project context. All API enablements and configurations are project-specific.  
**Access the Console:**  
1. Open your web browser (Chrome, Firefox, Safari, Edge)  
2. Navigate to: ++[https://console.cloud.google.com](https://console.cloud.google.com/)++  
3. Sign in with the same Google Account you used during gcloud init  
**Project Selection Process:**  
1. **Locate the Project Selector:**  
    * Look at the top navigation bar  
    * Near the left side, you’ll see a dropdown showing the current project name  
    * It typically appears as “[Project Name] ▼” or “Select a project ▼”  
2. **Open Project Selector:**  
    * Click on the project dropdown  
    * A modal window opens titled “Select a project”  
3. **Find Your Project:**  
    * You’ll see a list of projects you have access to  
    * Look for cyam-workspace-cli (or the variation you created)  
    * If you have many projects, use the search box at the top to filter  
4. **Select the Project:**  
    * Click on cyam-workspace-cli  
    * The modal closes  
    * The top navigation bar now displays “cyam-workspace-cli”  
**Visual Confirmation:**  
* Project name visible in top navigation bar  
* URL changes to include your project ID: https://console.cloud.google.com/?project=cyam-workspace-cli  
**Common Pitfalls:**  
* Working in the wrong project (enabling APIs in personal projects instead of CYAM project)  
* Not seeing the project (may need to wait a few minutes after creation for it to appear)  
* Multiple people on same Google Workspace domain seeing each other’s projects (normal for organizational accounts)  
  
**Step 2: Navigate to APIs & Services > Library**  
**Purpose and Context:**  
**Purpose and Context:**  
The API Library is where you discover and enable Google Cloud APIs. Each API must be explicitly enabled before your application can use it. This is a security and billing control mechanism.  
**Navigation Steps:**  
1. **Open the Navigation Menu:**  
    * Look for the “hamburger menu” icon (≡) in the top-left corner of the console  
    * Click it to open the main navigation sidebar  
2. **Locate APIs & Services:**  
    * Scroll down the navigation menu  
    * Look for the section labeled “APIs & Services”  
    * It may have a small icon resembling connected nodes or a plug  
3. **Select Library:**  
    * Click “APIs & Services” to expand the submenu (if collapsed)  
    * Click “Library” from the submenu options  
**Alternative Navigation Path:**  
* Some console versions have “APIs & Services” directly in the left sidebar  
* You can also use the search bar at the top: type “API Library” and select it from results  
**What You’ll See:**  
* The API Library page displays a searchable catalog of available Google APIs  
* Featured APIs appear at the top  
* Search bar for finding specific APIs  
* Categories for browsing (Machine Learning, Business, etc.)  
**Common Pitfalls:**  
* Navigating to “APIs & Services > Dashboard” instead of “Library” (Dashboard shows enabled APIs, Library shows all available)  
* Using browser back button and losing project context  
* Console interface variations between Google Workspace and Cloud Identity accounts  
  
**Step 3: Enable 5 APIs One by One**  
**Purpose and Context:**  
CYAM requires access to five specific Google Workspace services. Each service has a corresponding API that must be enabled. This step walks through enabling all five APIs individually.  
**APIs to Enable:**  
**APIs to Enable:**  
1. Google Sheets API  
2. Google Drive API  
3. Gmail API  
4. Google Calendar API  
5. Google Docs API  
**Enablement Process (Repeat for Each API):**  
**For Each API:**  
1. **Search for the API:**  
    * In the API Library page search bar, type the API name (e.g., “Google Sheets API”)  
    * Press Enter or click the search icon  
2. **Select the Correct API:**  
    * Click on the API card that matches exactly  
    * **Be specific**: “Google Sheets API” not “Sheets API v4” or similar variants  
    * The official Google APIs have blue Google logos  
3. **Enable the API:**  
    * You’ll see an API details page with description and documentation  
    * Look for the blue “Enable” button (usually prominent near the top)  
    * Click “Enable”  
4. **Wait for Enablement:**  
    * The page will show a loading indicator  
    * After 2-10 seconds, you’ll be redirected to the API’s dashboard/metrics page  
    * This confirms successful enablement  
5. **Return to Library:**  
    * Click “APIs & Services > Library” in the breadcrumb navigation at the top  
    * Or use the navigation menu to return to Library  
    * Search for and enable the next API  
**Verification - All APIs Enabled:**  
After enabling all five APIs:  
1. Navigate to “APIs & Services > Dashboard”  
2. You should see all five APIs listed under “Enabled APIs & services”  
3. Each should show “Enabled” status  
**Expected API List:**  
```
✓ Google Sheets API
✓ Google Drive API
✓ Gmail API
✓ Google Calendar API
✓ Google Docs API

```
**Common Pitfalls:**  
* Enabling wrong API variations (e.g., “Admin SDK API” instead of specific service APIs)  
* Not waiting for enablement to complete before moving to next API  
* Enabling APIs in wrong project (verify project name in top navigation bar)  
* Forgetting to enable all five APIs (common to miss one)  
  
## Task 4: Configure OAuth Credentials  
**Steps 1-7: OAuth Consent Screen Configuration**  
**Purpose and Context:**  
**Purpose and Context:**  
The OAuth consent screen is what users see when an application requests permission to access their Google account data. Configuring this screen is mandatory before creating OAuth credentials. This involves setting up the app identity, user type, and test user access.  
**Step 1: Navigate to APIs & Services > OAuth Consent Screen**  
1. Ensure cyam-workspace-cli is selected in the project dropdown  
2. Click “APIs & Services” in the navigation menu  
3. Select “OAuth consent screen” from the submenu  
**Step 2: Click “Get Started” If First Time**  
* If OAuth has never been configured for this project, you’ll see a “Get Started” or “Configure Consent Screen” button  
* Click it to begin the configuration wizard  
**Step 3: Set App Name and Contact Information**  
**App Information Section:**  
* **App name**: Enter exactly CYAM-Workspace-CLI  
* **User support email**: Select your email from the dropdown  
* **Developer contact information**: Enter your email address  
Click “Save and Continue”  
**Step 4: Click “Audience” Tab (or User Type Section)**  
Navigate to where you can configure the user type (Internal vs External)  
**Step 5: Click “Make External”**  
* Select “External” user type  
* This allows any Google Account user to authorize your application  
* Required for personal Gmail accounts and cross-organizational use  
**Step 6: Select “Testing” Publishing Status**  
* Choose “Testing” status (NOT “In Production”)  
* Testing status limits access to test users only  
* Avoids Google’s app verification requirements  
**Step 7: CRITICAL — Add Own Email to “Test Users”**  
1. Navigate to the “Test users” section/tab  
2. Click “Add users”  
3. Enter your complete Google Account email address  
4. Save the configuration  
**This is the most critical step** - without adding yourself as a test user, you’ll get “Access blocked: This app’s request is invalid” errors.  
  
**Steps 8-12: OAuth Credentials Creation and File Management**  
**Step 8: Navigate to Credentials**  
**Step 8: Navigate to Credentials**  
* Click “APIs & Services > Credentials” in the navigation menu  
**Step 9: Create OAuth Client ID > Desktop App**  
1. Click “+ CREATE CREDENTIALS”  
2. Select “OAuth client ID”  
3. For Application type, choose “Desktop app”  
4. Set a name (e.g., CYAM-Workspace-CLI-Desktop)  
5. Click “Create”  
**Step 10: Download the JSON File**  
* In the success modal, click “Download JSON”  
* File saves as client_secret_XXXXXXXXXXXXX.apps.googleusercontent.com.json  
**Step 11 & 12: Save JSON to Correct Location**  
**macOS Instructions:**  
```
mkdir -p ~/.config/gws
mv ~/Downloads/client_secret*.json ~/.config/gws/client_secret.json

```
**Windows Instructions (Comprehensive PowerShell):**  
```
# Create the directory structure
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.config\gws" | Out-Null

# Find the most recent client_secret file in Downloads
$SourceFile = Get-ChildItem -Path "$env:USERPROFILE\Downloads\client_secret*.json" | 
              Sort-Object LastWriteTime -Descending | 
              Select-Object -First 1

# Move and rename the file
if ($SourceFile) {
    Move-Item -Path $SourceFile.FullName -Destination "$env:USERPROFILE\.config\gws\client_secret.json" -Force
    Write-Host "Successfully moved client_secret.json to .config\gws\" -ForegroundColor Green
} else {
    Write-Host "Error: No client_secret*.json file found in Downloads folder" -ForegroundColor Red
}

```
**Windows Alternative Manual Method:**  
1. Open File Explorer  
2. Navigate to %USERPROFILE% (type this in address bar)  
3. Create .config folder, then gws subfolder inside it  
4. Copy the downloaded JSON file into the gws folder  
5. Rename to exactly client_secret.json  
**Verification Commands:**  
**macOS:**  
**macOS:**  
```
ls -la ~/.config/gws/client_secret.json

```
**Windows:**  
```
Test-Path "$env:USERPROFILE\.config\gws\client_secret.json"
Get-Item "$env:USERPROFILE\.config\gws\client_secret.json" | Format-List

```
  
## Task 5: Verify Workspace CLI Connection  
**Step 1: Open Terminal or PowerShell**  
**macOS**: Open Terminal (Applications > Utilities > Terminal)**Windows**: Open PowerShell (regular user mode is sufficient)  
**Step 2: Run Authentication Command**  
**Command:**  
```
gws auth login --services drive,gmail,sheets

```
**Windows-Specific Execution Policy Check:**  
If you encounter an error like “execution of scripts is disabled on this system”:  
```
# Check current execution policy
Get-ExecutionPolicy -Scope CurrentUser

# If it shows "Restricted" or "Undefined", change it:
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Type 'Y' when prompted, then retry the gws command
gws auth login --services drive,gmail,sheets

```
**Steps 3-5: Browser Authentication Flow**  
**Automatic Browser Opening:**  
* Browser should open to Google’s OAuth authorization page  
* Sign in with the same email you added as a test user  
* You may see “Google hasn’t verified this app” - click “Advanced” then “Go to CYAM-Workspace-CLI (unsafe)”  
* Click “Allow” to grant permissions  
**Manual Browser Opening (if automatic fails):**  
* Copy the entire URL from terminal starting with https://accounts.google.com/o/oauth2/...  
* Paste into browser manually  
* Complete authentication flow  
* Return to terminal  
**Steps 6-7: Verification Commands**  
**Primary Verification:**  
```
gws drive files list --params '{"pageSize": 5}'

```
**Windows PowerShell JSON Syntax Alternative:**If the above fails on Windows due to quote handling:  
```
gws drive files list --params "{`"pageSize`": 5}"

```
**Expected Success Output:**  
```
{
  "kind": "drive#fileList",
  "incompleteSearch": false,
  "files": [
    {
      "kind": "drive#file",
      "id": "1a2b3c4d5e6f7g8h9i0j",
      "name": "My Document",
      "mimeType": "application/vnd.google-apps.document"
    }
  ]
}

```
**Additional Verification Commands:**  
**Test Gmail Access:**  
**Test Gmail Access:**  
```
gws gmail messages list --params '{"maxResults": 5}'

```
**Test Sheets Access:**  
```
gws sheets spreadsheets list --params '{"pageSize": 5}'

```
  
## 3. Common Edge Cases & Troubleshooting  

| Symptom/Error | Diagnostic Questions | Resolution Steps |
| --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| “Access blocked: This app’s request is invalid” during OAuth | 1. Did you add your email to Test Users in OAuth consent screen?
2. Are you signing in with the exact email address you added?
3. Is the app publishing status set to “Testing”? | Step 1: Navigate to Google Cloud Console > APIs & Services > OAuth consent screen
Step 2: Click “Test users” tab
Step 3: Verify your email is listed. If not, click “+ Add Users” and add your exact Google Account email
Step 4: Click “Save”
Step 5: Return to terminal and retry gws auth login
Step 6: When browser opens, sign in with the exact email you added as test user |
| gcloud: command not found (Windows) | 1. Did you restart PowerShell after installation?
2. Did the installer complete successfully?
3. Are you using the correct shell? | Step 1: Close all PowerShell windows
Step 2: Open new PowerShell window
Step 3: Test with gcloud --version
Step 4: If still failing, search Start menu for “Google Cloud SDK Shell” and use that instead
Step 5: Check PATH manually: `$env:PATH -split ‘;’ |
| gcloud: command not found (macOS) | 1. Did you answer ‘Y’ to PATH modification during install?
2. Are you using a fresh terminal window?
3. Which shell are you using (bash/zsh)? | Step 1: Close all Terminal windows
Step 2: Open a brand new Terminal window
Step 3: Test with gcloud --version
Step 4: If still failing, manually source: source "$HOME/google-cloud-sdk/path.zsh.inc"
Step 5: To make permanent: echo 'source "$HOME/google-cloud-sdk/path.zsh.inc"' >> ~/.zshrc
Step 6: Restart terminal and test again |
| npm: command not found when installing Workspace CLI | 1. Did you install Node.js before attempting this step?
2. Did you open a fresh terminal after installing Node.js?
3. What does node -v return? | Step 1: Verify Node.js installation: node -v
Step 2: If “command not found”, install Node.js from https://nodejs.org/en/download (choose LTS version)
Step 3: (Windows) During installation, ensure “Add to PATH” is checked
Step 4: Close and reopen terminal/PowerShell
Step 5: Verify npm: npm -v
Step 6: Retry Workspace CLI installation: npm install -g @googleworkspace/cli |
| “Execution of scripts is disabled” (Windows PowerShell) | 1. Are you getting this error when running gws commands?
2. What does Get-ExecutionPolicy -Scope CurrentUser return?
3. Are you in a corporate environment with restricted policies? | Step 1: Check current policy: Get-ExecutionPolicy -Scope CurrentUser
Step 2: If “Restricted” or “Undefined”, change it: Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Step 3: Type ‘Y’ when prompted to confirm
Step 4: Retry the gws command
Step 5: If corporate policy prevents changes, use Command Prompt instead of PowerShell
Step 6: Alternative: Run PowerShell as Administrator and set system-wide policy |
| Password prompt appears but nothing happens when typing (macOS) | 1. Are you seeing “Password:” prompt during installation?
2. Did you try typing even though nothing appears?
3. Are you using the correct macOS login password? | Explanation: This is normal macOS security behavior for sudo commands
Step 1: When you see “Password:” prompt, type your macOS login password
Step 2: Characters won’t appear on screen - this is intentional security
Step 3: Press Enter after typing password
Step 4: If incorrect, you’ll see “Sorry, try again” - retype carefully
Step 5: You have 3 attempts before the command fails |
| gws auth login hangs or doesn’t open browser | 1. Did you wait at least 30 seconds?
2. Is there a URL displayed in the terminal?
3. Are you behind a corporate firewall?
4. Does gws --version work? | Step 1: Wait 30 seconds - OAuth request can be slow
Step 2: Look for URL starting with https://accounts.google.com/o/oauth2/...
Step 3: If URL displayed, copy entire URL and paste into browser manually
Step 4: If no URL and command hangs: Press Ctrl + C, verify internet: ping google.com
Step 5: Check client_secret.json exists: (macOS) ls ~/.config/gws/client_secret.json (Windows) Test-Path "$env:USERPROFILE\\.config\\gws\\client_secret.json"
Step 6: For corporate networks, configure proxy settings |
| “Client secret file not found” error | 1. Did you complete Task 4, Steps 10-12?
2. Is the file in the exact correct location?
3. Is the filename exactly client_secret.json? | Step 1: Verify file exists:
(macOS) ls -la ~/.config/gws/client_secret.json
(Windows) Test-Path "$env:USERPROFILE\\.config\\gws\\client_secret.json"
Step 2: If missing, locate downloaded JSON in Downloads folder
Step 3: Recreate directory and move file:
(macOS) mkdir -p ~/.config/gws && mv ~/Downloads/client_secret*.json ~/.config/gws/client_secret.json
(Windows) Use PowerShell commands from Task 4, Step 12
Step 4: Verify filename is exactly client_secret.json |
| “API has not been enabled” errors | 1. Which specific API is mentioned in the error?
2. Did you enable all 5 APIs in Task 3?
3. Are you in the correct Google Cloud project? | Step 1: Note which API is mentioned (Drive, Gmail, Sheets, etc.)
Step 2: Go to Google Cloud Console: https://console.cloud.google.com
Step 3: Verify correct project selected (cyam-workspace-cli)
Step 4: Navigate to APIs & Services > Dashboard
Step 5: Check if the mentioned API is in “Enabled APIs & services” list
Step 6: If missing, go to APIs & Services > Library
Step 7: Search for and enable the specific API
Step 8: Wait for enablement to complete, then retry CLI command |
| JSON parsing errors in Windows PowerShell | 1. Are you getting syntax errors with the --params flag?
2. Are you using single quotes around JSON?
3. Is PowerShell interpreting the JSON incorrectly? | Step 1: Replace single quotes with escaped double quotes:
Instead of: --params '{"pageSize": 5}'
Use: --params "{"pageSize": 5}"
Step 2: Alternative - use Command Prompt instead of PowerShell for JSON commands
Step 3: Or save JSON to file and reference: --params @params.json
Step 4: Verify JSON syntax with online validator if needed |
  
## 4. Fallback URL Routing  
When users encounter issues beyond standard troubleshooting or require deeper technical information, direct them to these authoritative resources:  
1. **Google Cloud CLI Installation Guide:**++[https://cloud.google.com/sdk/docs/install](https://cloud.google.com/sdk/docs/install)++*Comprehensive installation instructions for all platforms, system requirements, and installation verification*  
2. **Google Workspace CLI GitHub Repository:**++[https://github.com/googleworkspace/gws-cli](https://github.com/googleworkspace/gws-cli)++*Official source code, documentation, issue tracker, and community support for the Workspace CLI*  
3. **Node.js Installation Resources:**++[https://nodejs.org/en/download/](https://nodejs.org/en/download/)++*Official Node.js downloads for all platforms, installation guides, and version information*  
4. **OAuth Consent Screen Documentation:**++[https://support.google.com/cloud/answer/10311615](https://support.google.com/cloud/answer/10311615)++*Detailed guide on configuring OAuth consent screens, user types, verification requirements, and publishing status*  
5. **Google API Library and Enablement:**++[https://console.cloud.google.com/apis/library](https://console.cloud.google.com/apis/library)++*Direct link to API Library for discovering and enabling Google Cloud and Workspace APIs*  
6. **Google Cloud CLI Initialization Guide:**++[https://cloud.google.com/sdk/docs/initializing](https://cloud.google.com/sdk/docs/initializing)++*Step-by-step guide for gcloud init, authentication options, and configuration management*  
7. **PowerShell Execution Policy Documentation:**++[https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies)++*Microsoft’s official documentation on PowerShell execution policies and security settings*  
  
## 5. Unlisted Constraints & Platform Limitations  
**Critical “DO NOT DO THIS” Rules - Chatbot Must Aggressively Enforce:**  
## OAuth and Security Constraints:  
1. **NEVER instruct users to select “In production” for OAuth publishing status.** Always use “Testing” status for CYAM installations. Production status requires Google verification (weeks-long process), privacy policy, terms of service, and security review.  
2. **NEVER allow users to skip adding themselves as Test Users.** This is the #1 cause of “Access blocked” errors. Aggressively remind users that OAuth apps in Testing status REQUIRE explicit test user allowlisting.  
3. **NEVER instruct users to share client_secret.json or credentials.json files.** These contain sensitive authentication credentials equivalent to passwords.  
4. **NEVER suggest using service account credentials instead of user OAuth credentials for this workflow.** Service accounts are for server-to-server applications, not interactive CLI tools.  
5. **NEVER instruct users to grant more OAuth scopes than necessary.** The --services drive,gmail,sheets flag is sufficient for CYAM.  
## Installation and Configuration Constraints:  
1. **NEVER recommend unofficial installation sources.** Only direct users to official sites: ++[cloud.google.com](http://cloud.google.com/)++ for Google Cloud CLI, ++[npmjs.com](http://npmjs.com/)++ for Workspace CLI, ++[python.org](http://python.org/)++ for Python, ++[nodejs.org](http://nodejs.org/)++ for Node.js.  
2. **NEVER suggest modifying system PATH manually as a first troubleshooting step.** Official installers handle PATH configuration automatically.  
3. **NEVER instruct users to run installers with sudo/administrator privileges unless the installer itself explicitly prompts for it.**  
4. **NEVER suggest installing Python versions older than 3.8.** Google Cloud CLI requires Python 3.8+.  
5. **NEVER instruct users to install Node.js “Current” version when “LTS” is available.** LTS versions are more stable.  
## Windows-Specific Constraints:  
1. **NEVER ignore Windows PowerShell Execution Policy issues.** Always address execution policy restrictions before attempting to run npm-installed CLI tools.  
2. **NEVER instruct Windows users to modify system-wide execution policies without explaining the security implications.**  
3. **NEVER suggest using Command Prompt when PowerShell-specific features are needed, but DO suggest Command Prompt as an alternative when PowerShell execution policies are problematic.**  
4. **NEVER assume Windows file paths work the same as Unix paths.** Always use Windows-appropriate environment variables like $env:USERPROFILE.  
## File and Directory Constraints:  
1. **NEVER instruct users to place client_secret.json in arbitrary locations.** Must be in ~/.config/gws/ (macOS) or %USERPROFILE%\.config\gws\ (Windows).  
2. **NEVER suggest renaming client_secret.json to anything else.** The Workspace CLI hardcodes this filename.  
3. **NEVER instruct users to manually edit JSON credential files.**  
## Project and Resource Constraints:  
1. **NEVER instruct users to delete or modify the cyam-workspace-cli project after creation.**  
2. **NEVER suggest creating multiple Google Cloud projects for this workflow.**  
3. **NEVER instruct users to enable billing during initial setup.** Google Workspace APIs are free for reasonable personal use.  
## Scope and User Experience Constraints:  
1. **NEVER provide more than 4-5 troubleshooting steps at once.** Provide steps incrementally based on results.  
2. **NEVER assume the user’s operating system.** Always clarify macOS vs Windows when instructions differ significantly.  
3. **NEVER blame users for errors.** Frame all troubleshooting as collaborative problem-solving.  
4. **NEVER use technical jargon without explanation.** Always explain terms like “PATH variable,” “OAuth flow,” etc.  
5. **NEVER provide guidance on CYAM Platform configuration during this workflow.** This is strictly CLI setup only.  
  
## Additional Windows Deep-Dive Section  
## Windows Environment Setup and Troubleshooting  
**PowerShell vs Command Prompt Decision Matrix**  
**Use PowerShell When:**  
* Installing npm packages globally (better error handling)  
* Working with environment variables ($env:USERPROFILE)  
* Need advanced scripting capabilities  
* Using modern Windows features  
**Use Command Prompt When:**  
* PowerShell execution policies are restricted  
* Corporate environment blocks PowerShell scripts  
* Simple file operations  
* Compatibility with older Windows systems  
**Windows-Specific File Path Handling**  
**Environment Variables:**  
```
# User profile directory
$env:USERPROFILE  # Equivalent to ~ on Unix

# Program Files locations
$env:ProgramFiles      # Usually C:\Program Files
${env:ProgramFiles(x86)}  # Usually C:\Program Files (x86)

# AppData locations  
$env:APPDATA          # Roaming profile data
$env:LOCALAPPDATA     # Local profile data

```
**Hidden Folder Creation:**  
```
# Create .config folder (Windows may warn about leading dot)
New-Item -Path "$env:USERPROFILE\.config" -ItemType Directory -Force

# Verify folder exists and is accessible
Test-Path "$env:USERPROFILE\.config"
Get-Item "$env:USERPROFILE\.config" -Force  # -Force shows hidden items

```
**Windows Execution Policy Management**  
**Check Current Policies:**  
**Check Current Policies:**  
```
# Check all execution policy scopes
Get-ExecutionPolicy -List

# Check specific scope
Get-ExecutionPolicy -Scope CurrentUser
Get-ExecutionPolicy -Scope LocalMachine

```
**Safe Policy Changes:**  
```
# Safest option - only affects current user
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# More restrictive alternative
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser

# Verify change
Get-ExecutionPolicy -Scope CurrentUser

```
**Windows npm Global Package Management**  
**Check Global Installation Location:**  
```
# Find npm global directory
npm config get prefix

# List global packages
npm list -g --depth=0

# Check if global bin directory is in PATH
$env:PATH -split ';' | Where-Object { $_ -like "*npm*" }

```
**Fix Global Package PATH Issues:**  
```
# Get npm global bin directory
$npmGlobalBin = "$(npm config get prefix)"

# Add to current session PATH (temporary)
$env:PATH += ";$npmGlobalBin"

# Add to user PATH permanently (requires new session)
[Environment]::SetEnvironmentVariable("PATH", $env:PATH + ";$npmGlobalBin", "User")

```
**Windows File Association and Default Applications**  
**Browser Opening Issues:**  
**Browser Opening Issues:**  
```
# Check default browser
Get-ItemProperty HKCU:\Software\Microsoft\Windows\Shell\Associations\UrlAssociations\http\UserChoice

# Test if browser can be opened programmatically
Start-Process "https://www.google.com"

```
**File Extension Handling:**  
```
# Verify .json files aren't hidden by extension hiding
Get-ItemProperty "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" -Name "HideFileExt"

# Show file extensions (if needed)
Set-ItemProperty "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" -Name "HideFileExt" -Value 0

```
**Windows Network and Proxy Configuration**  
**Corporate Network Diagnostics:**  
```
# Test basic connectivity
Test-NetConnection google.com -Port 443
Test-NetConnection npmjs.com -Port 443

# Check proxy settings
netsh winhttp show proxy

# Configure npm for corporate proxy
npm config set proxy http://proxy.company.com:8080
npm config set https-proxy https://proxy.company.com:8080
npm config set registry https://registry.npmjs.org/

```
**Windows Security and Antivirus Considerations**  
**Windows Defender Exclusions:**  
```
# Check if Windows Defender is blocking npm operations
Get-MpPreference | Select-Object -Property ExclusionPath, ExclusionProcess

# Add npm directories to exclusions (run as Administrator)
Add-MpPreference -ExclusionPath "C:\Program Files\nodejs"
Add-MpPreference -ExclusionPath "$env:APPDATA\npm"

```
**Corporate Antivirus Troubleshooting:**  
* Temporarily disable real-time scanning during installation  
* Add npm and gws executables to antivirus exceptions  
* Check corporate policy for software installation restrictions  
* Contact IT department for whitelist approval if needed  
This comprehensive Windows deep-dive provides the detailed Windows-specific guidance requested, ensuring users on Windows platforms have robust support for every aspect of the CLI setup process.  
