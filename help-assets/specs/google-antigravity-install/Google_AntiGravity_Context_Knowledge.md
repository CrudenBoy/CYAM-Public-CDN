# Google AntiGravity - Implementation Knowledge & Related Topics

This document provides supplementary context for the Google AntiGravity IDE, focused on macOS installation and broader learning resources.

## Related Learning Topics
*   **Google Developers Codelabs**: [Home Page](https://codelabs.developers.google.com/) | [Getting Started Codelab](https://codelabs.developers.google.com/getting-started-google-antigravity)
*   **YouTube Tutorial Playlist**: [View Playlist](https://www.youtube.com/playlist?list=PLuT8wfgyV8tjGHAYNHJ9wPES3BEq-TnKN)

---

## AntiGravity Setup Checklist (10-Second Scan)

| Required | Optional / Changeable Later |
| :--- | :--- |
| **Supported OS** (macOS 12+ Silicon, Win 10, Linux) | **Keybindings** |
| **Google Chrome browser** | **Extensions** |
| **Google Account** (Personal or Workspace) | **Command Line (`agy`)** |
| **Install the desktop app & sign in** | **Terminal & Review Policies** (changeable later) |
| **Chrome Extension** (only if using browser agent) | **JavaScript Execution Policy** (changeable later) |

*My recommendation if you want the simplest path:*
If you just want AG running, do the basics first: install the app, sign in, and skip worrying too much about keybindings, extensions, or agy. If you are a developer planning to use AG heavily, treat extensions and the browser extension as highly recommended, and the command line tool as useful if you like working from Terminal.

---

## Detailed Setup Context & Explanations

### What you need before you start — these are the real prerequisites
* **A supported computer**: Antigravity needs to be installed on your own machine. Official docs say it supports macOS, Windows 10 (64-bit), and certain Linux systems. On Mac, the docs say it supports newer versions that still receive Apple security updates, with macOS 12 Monterey minimum, and Intel/X86 Mac is not supported. On Linux, it needs certain system libraries, so it is more of a “developer setup” than a casual install.
* **Google Chrome**: The codelab says you need Chrome. This is important because Antigravity’s browser features rely on Chrome and its extension. If you do not have Chrome, you can’t use the browser automation part.
* **A Google Account**: The codelab says Antigravity preview is available for personal Gmail accounts, but you can also access it with a supported organizational Google Workspace account. In plain terms, that means you need a regular Google account you can sign into.

### What is required to actually install and start using AG
* **Download and install the Antigravity app**: This is the actual installation step. Without the desktop app, you do not have AG installed.
* **Launch the app and sign in**: The codelab shows that after installation, you go through setup and then sign in to Google. Practically speaking, if you want to use AG as described in the codelab, signing in is part of getting it running.
* **Choose your initial safety / autonomy settings**: During setup, AG asks how much freedom the agent has to run terminal commands, whether it should ask for review, and whether it can run JavaScript in the browser. These are important operational settings, but the codelab also says they can be changed later in Settings. So they matter, but they are not permanent choices.

### What is optional during setup — useful, but not required to install AG
* **Keybindings**: This is just the keyboard shortcut style AG will use in the editor. Think of it as choosing whether the app should “feel like” another editor you already know.
* **Extensions**: These are editor add-ons, like language support packs and coding helpers. They improve your coding experience. Not required to install AG itself.
* **Command Line (agy)**: This installs a terminal command called agy. It lets you open Antigravity from the command line instead of manually opening the app.

### The browser extension — important distinction
* **What it is**: A Chrome extension that lets Antigravity control the browser, such as opening pages, clicking buttons, scrolling, reading web content, and validating UI flows.
* **Is it required?** Required for browser automation features: Yes. Required to install AG at all? No.

### The safety settings during onboarding — what they really mean
* **Terminal Execution policy**: Controls whether AG can run terminal commands automatically or must ask first. Balances convenience against safety.
* **Review policy**: Controls whether AG asks you to review plans and work artifacts.
* **JavaScript Execution policy**: Controls whether AG can run browser-side JavaScript when using browser tools.

**Sources:**
* Google Codelab: https://codelabs.developers.google.com/getting-started-google-antigravity
* Official docs: https://antigravity.google/docs
* Download page: https://antigravity.google/download

---
*Context for AntiGravity Chatbot — Last Updated March 2026*
