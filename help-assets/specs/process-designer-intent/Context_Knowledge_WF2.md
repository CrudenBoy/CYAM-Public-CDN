# CYAM Workflow Platforms: Matchmaking Matrix

This document is used by the Intent Mapping & Tool Assessment Help Bot to determine the ideal execution platform for a given process based on the user's technical capability and workspace constraints.

## 1. Google Apps Script (Custom Code)
- **IDEAL_USER_SKILL**: Advanced Developer
- **ACCOUNT_REQUIREMENT**: Works on both free consumer Gmail and paid Google Workspace accounts.
- **COST_IMPLICATION**: Strictly free, leveraging the infrastructure already included in your standard Google account.
- **SETUP_FRICTION**: Medium - Access the cloud-based IDE directly from your browser with zero installation, though it requires actual coding logic from scratch.
- **THE_PITCH**: Achieve ultimate flexibility and bespoke automation across the entire Google ecosystem by writing tailored code without paying for third-party subscription tools.
- **THE_WARNING**: Hard-coded scripts create technical debt and maintenance bottlenecks for non-technical teams if the original developer leaves your organization.
- **BEST_ALTERNATIVE**: Google Workspace Studio (Flows)

## 2. Google Opal (Standard SOPs)
- **IDEAL_USER_SKILL**: No-code Beginner / Business Operations User
- **ACCOUNT_REQUIREMENT**: Works natively on both free consumer Gmail and paid Google Workspace accounts.
- **COST_IMPLICATION**: Strictly free (currently in experimental beta).
- **SETUP_FRICTION**: Low - Utilizes conversational language to automatically generate visual workflow steps instantly with zero configuration or installation required.
- **THE_PITCH**: Empower frontline workers to instantly digitize, track, and automate their daily standard operating procedures simply by describing them in plain English.
- **THE_WARNING**: Because it abstracts the underlying architecture into a simple visual tool, it is not ideal for complex, deterministic data pipelines that require rigid programmatic precision.
- **BEST_ALTERNATIVE**: Google Workspace Studio (Flows)

## 3. Google Workspace Studio (Flows)
- **IDEAL_USER_SKILL**: Low-code Business Analyst / Process Admin
- **ACCOUNT_REQUIREMENT**: Requires a paid Google Workspace Business or Enterprise account.
- **COST_IMPLICATION**: Bundled entirely within your existing enterprise Google Workspace license at no extra base cost (subject to workspace add-on conditions).
- **SETUP_FRICTION**: Medium - Offers a highly intuitive visual layout directly inside Workspace, but requires an understanding of basic variables, inputs/outputs, and data mapping.
- **THE_PITCH**: Visually orchestrate secure, cross-application corporate workflows utilizing Gemini's reasoning capabilities to handle dynamic business decisions natively.
- **THE_WARNING**: You must be operating within a paid corporate Workspace environment to access it, and complex multi-step flows can become difficult to troubleshoot compared to clean code.
- **BEST_ALTERNATIVE**: Google Apps Script (Custom Code)

## 4. Google Workspace Studio CLI (Experimental)
- **IDEAL_USER_SKILL**: CLI Power User / DevOps Engineer
- **ACCOUNT_REQUIREMENT**: Requires a Google account with access to Google Workspace and a Google Cloud project to set up OAuth credentials.
- **COST_IMPLICATION**: Free and open source (bundled entirely within your existing Workspace license and GCP quota).
- **SETUP_FRICTION**: High - Requires local terminal installation (e.g., `npm install`), a Google Cloud project, strict manual authentication configuration (`gws auth setup`), and command-line proficiency.
- **THE_PITCH**: Bring enterprise-grade governance and infrastructure-as-code principles to your internal automation strategy by interacting with any Google Workspace API dynamically from your terminal.
- **THE_WARNING**: The complete lack of a graphical interface and highly technical setup makes this tool entirely inaccessible to everyday business users and citizen developers.
- **BEST_ALTERNATIVE**: Google Workspace Studio (Flows) or Google Apps Script.

## 5. Google AI Studio
- **IDEAL_USER_SKILL**: AI Developer / Prompt Engineer
- **ACCOUNT_REQUIREMENT**: Works universally on both free consumer Gmail and paid Google Workspace accounts.
- **COST_IMPLICATION**: Pay-as-you-go API consumption costs based strictly on token usage, with a generous free tier available for initial prototyping.
- **SETUP_FRICTION**: Medium - It is incredibly easy to prototype prompts in the browser, but integrating those outputs into a live business workflow requires custom engineering (API calls).
- **THE_PITCH**: Rapidly prototype, tune, and deploy Google's cutting-edge generative AI models directly into your custom business applications to drive unprecedented efficiency.
- **THE_WARNING**: It is an AI model testing playground rather than a ready-made automation runner, meaning it cannot autonomously execute business tasks across apps without external software wrapping it.
- **BEST_ALTERNATIVE**: Google Apps Script (Custom Code)
