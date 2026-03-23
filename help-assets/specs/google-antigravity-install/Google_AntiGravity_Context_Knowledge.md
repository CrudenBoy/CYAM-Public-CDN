# Google AntiGravity - Implementation Knowledge & Related Topics

This document provides supplementary context for the Google AntiGravity IDE, focused on macOS installation and broader learning resources.

## Related Learning Topics

The following resources provide additional training and documentation for AntiGravity:

*   **Google Developers Codelabs**: Access structured, hands-on coding tutorials for AntiGravity and other Google technologies.
    - [Home Page](https://codelabs.developers.google.com/)
    - [Getting Started Codelab](https://codelabs.developers.google.com/getting-started-google-antigravity)

*   **YouTube Tutorial Playlist**: A curated collection of video walkthroughs for setting up and using AntiGravity.
    - [View Playlist](https://www.youtube.com/playlist?list=PLuT8wfgyV8tjGHAYNHJ9wPES3BEq-TnKN)

## Key Technical Concepts

### Agent Autonomy Policies
AntiGravity introduces several safety layers for AI agent execution:
1. **Secure Mode**: Zero terminal access for agents.
2. **Review-Driven (Recommended)**: Agent can write and propose commands, but the user must click "Run" in the UI.
3. **Agent-Driven**: Agent can execute commands autonomously within a sandboxed environment.

### The `agy` CLI
The `agy` tool is the command-line interface used by both human developers and AI agents to manipulate the workspace, manage dependencies, and trigger agentic workflows.

---

## Detailed Setup Instructions

2. Installation
If you don't have Antigravity installed already, let's begin with installing Antigravity. Currently the product is available for preview and you can use your personal Gmail account to get started with it.

Go to the downloads page and click on the appropriate operating system version that is applicable to your case. Launch the application installer and install the same on your machine. Once you have completed the installation, launch the Antigravity application. You should see a screen similar to the following:

Please proceed with clicking on Next each time. Key steps are detailed below:

Choose setup flow: This brings up the option for you to import from your existing VS Code or Cursor settings. We will go with a fresh start.
Choose an Editor theme type: We will go with the dark theme but it's entirely up to you.
How do you want to use the Antigravity agent?

Let's understand this in a bit more detail. Remember that settings can be changed at any time via Antigravity User Settings (Cmd + ,).

Before we delve into the options, let us look at some specific properties (which you see to the right of the dialog).

Terminal Execution policy
This is about giving the Agent the ability to execute commands (applications/tools) in your terminal:

Always proceed: Always auto-execute terminal commands (except those in a configurable deny list).
Request review: Request user review and approval before executing terminal commands.

Review policy
As the Agent goes about its task, it creates various artifacts (task plan, implementation plan, etc). The review policy is set such that you can determine who decides if it needs to be reviewed. Should you always want to review it, or let the agent decide on this. Accordingly, there are three options here too.

Always Proceed: Agent never asks for review.
Agent Decides: Agent will decide when to ask for review.
Request Review: Agent always asks for review.

JavaScript Execution policy
When enabled, the agent can use browser tools to open URLs, read web pages, and interact with browser content. This policy controls how JavaScript is executed in the browser.

Always Proceed: Agent will not stop to ask for permission to run Javascript in the browser. This provides the Agent with maximum autonomy to perform complex actions and validation in the browser, but also has the highest exposure to security exploits.
Request review: Agent will always stop to ask for permission to run Javascript code in the browser.
Disabled: Agent will never run Javascript code in the browser.

Now that we have understood different policies, the 4 options on the left are nothing but specific settings for the terminal execution, review, and JavaScript execution policies for 3 of them and a 4th option available where we can completely custom control it. These 4 options are available so that we can choose how much autonomy you want to give to the Agent to execute commands in the terminal and get artifacts reviewed before moving ahead with the task.

These 4 options are:

Secure mode: Secure Mode provides enhanced security controls for the Agent, allowing you to restrict its access to external resources and sensitive operations. When Secure Mode is enabled, several security measures are enforced to protect your environment.
Review-driven development (recommended): The agent will frequently ask for review.
Agent-driven development: The agent will never ask for review.
Custom configuration

The Review-driven development option is a good balance and the recommended one since it allows the agent to make a decision and come back to the user for approval.

Next is the Configure your Editor settings page where you can choose your preferences for the following:

Keybindings: Configure your keybindings.
Extensions: Install popular language and other recommended extensions.
Command Line: Install the command line tool to open Antigravity with agy.

Now, you're ready to Sign in to Google. As mentioned earlier, Antigravity is available in preview mode and free if you have a personal Gmail account. Sign in now with your account. This will open up the browser allowing you to sign in. On successful authentication, you will see a message similar to the one below and it will lead you back to the Antigravity application. Go with the flow.

Finally, Terms of Use. You can make a decision if you'd like to opt-in or not and then click on Next.

This will lead you to the moment of truth, where Antigravity will be waiting to collaborate with you.

**Note:** There are two links the user can use for further information about AntiGravity:
* YouTube: https://www.youtube.com/playlist?list=PLuT8wfgyV8tjGHAYNHJ9wPES3BEq-TnKN
* Codelabs: https://codelabs.developers.google.com/getting-started-google-antigravity#0

---
*Context for AntiGravity Chatbot — Last Updated March 2026*
