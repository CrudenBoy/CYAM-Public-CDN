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
*Context for AntiGravity Chatbot — Last Updated March 2026*
