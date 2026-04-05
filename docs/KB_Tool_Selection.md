# CYAM Tool Constraints Registry

**Last_Updated:** April 4, 2026

## 1. Google Apps Script
*   **Script Execution Maximum Time:** 6 minutes per execution (up to 30 minutes for select Google Workspace Enterprise tiers). Custom functions in Sheets are strictly limited to 30 seconds per execution.
*   **URL Fetch App Payload Size Limits:**
    *   Response Data: 50 MB per call.
    *   POST Data: 50 MB per call.
    *   Headers: Maximum of 100 headers per call; 8 KB maximum size per header.
    *   URL Length: Maximum 2 KB (2,048 characters) per call.
*   **Simultaneous Executions:** 30 concurrent executions per user.

## 2. HubSpot CRM
*   **Standard API Rate Limits (Private Apps):**
    *   Free/Starter: 100 requests per 10 seconds; 250,000 daily requests.
    *   Professional/Enterprise: 190 requests per 10 seconds; up to 1,000,000 daily requests.
*   **Standard API Rate Limits (Public OAuth Apps):** 110 requests per 10 seconds.
*   **Webhook Constraints & Payload Sizes:**
    *   Batch Size: HubSpot batches up to 100 events per single webhook request.
    *   Execution Timeout: HubSpot enforces a strict 5-second timeout for the receiving endpoint to acknowledge the webhook (otherwise it queues for retry).
    *   Timeline Events Payload: 1 MB maximum total size per serialized event instance (510 KB per property/token limit).

## 3. Slack API
*   **Block Kit UI Payload Size Limits:**
    *   Overall Payload Size: 16 KB maximum per message (the server disconnects clients sending JSON payloads larger than this).
    *   Block Count: Maximum 50 blocks in standard messages; maximum 100 blocks in Modals or Home tabs.
    *   Character Limit: Recommended maximum of 4,000 characters for standard channel message texts.
*   **Tier-Based API Rate Limits:**
    *   Tier 1: 1+ request per minute (e.g., conversations.history for unlisted/non-Marketplace apps).
    *   Tier 2: 20+ requests per minute.
    *   Tier 3: 50+ requests per minute.
    *   Tier 4: 100+ requests per minute (generous burst behavior).
*   **Posting Messages:** Strictly 1 message per second per channel (bursting allowed, but delivery is not guaranteed if sustained).
*   **Events API:** Capped at 30,000 deliveries per workspace/team per app per 60 minutes.

## 4. Google AI Studio (Gemini API)
*   **Maximum Context Window Limits:**
    *   Gemini 2.5 / 3.x Pro Models: 1,000,000 (1M) tokens context window.
    *   Gemini 2.5 / 3.x Flash Models: 1,000,000 (1M) tokens context window.
    *   Image/Preview Models: Cap at 32k to 128k context windows depending on specific versions.
*   **Free-Tier Caps (Per Project):**
    *   Tokens Per Minute (TPM): 250,000 TPM limit shared across all free models.
    *   Gemini 2.5 Pro: 5 RPM / 100 RPD (Requests Per Day).
    *   Gemini 2.5 Flash: 10 RPM / 500 RPD.
    *   Gemini 2.5 Flash-Lite: 15 RPM / 1,000 RPD.
*   **Paid-Tier Caps (Varies by Spending Tier):**
    *   Tier 1: 150 RPM (Pro) / 300 RPM (Flash); 1M-2M TPM.
    *   Tier 2: 1,000 RPM (Pro) / 2,000 RPM (Flash); 2M-4M TPM.
    *   Tier 3: Up to 4,000+ RPM and Unlimited RPD.

## 5. Zapier & Make.com (Integromat)
*   **Zapier Execution & Payload Constraints:**
    *   Execution Timeout: 30 seconds maximum for any single Zap step, trigger, or action (including "Code by Zapier").
    *   Webhook Ingestion Payload Size: 10 MB maximum for Catch Hooks (Triggers), 5 MB for actions, and 2 MB for Raw Webhooks.
*   **Make.com Execution & Payload Constraints:**
    *   Execution Timeout: 40 minutes per scenario (with a strict 5-minute absolute grace period, forcing a hard kill at 45 minutes).
    *   Webhook Ingestion Payload Size: 5 MB (5,242,880 bytes) content-length limit.

## 6. Google AppSheet
*   **Automation Execution Constraints:**
    *   Max Scheduled Event Execution Time: 5 minutes.
    *   Max App Event Execution Time: 2 minutes.
    *   Max Concurrent Bots: 5,000.
    *   Max Wait State Duration: 30 days.
*   **API & Processing Rate Limits:**
    *   100,000 'Wait' steps executed per day (2,000 per 20 mins).
    *   500,000 process executions triggered by scheduled/app events per day.
*   **Cell Processing & Database Maximums:**
    *   Cell Limits: 2,000 characters per standard cell; 5,000 characters per LongText column.
    *   Payload Limit: 10 MB maximum data size of a table record processed by a bot.
    *   Database Capacity: Free (1,000 rows); Core/Starter (2,500 rows); Enterprise Plus (200,000 rows per database).
    *   Sync Target Limit: Under 5-10 MB total compressed app data to avoid excessive sync timeout degradation.

## 7. Google Cloud Access Context Manager (Google Opal)
*   **API Rate Limits:**
    *   Read Requests: 500 requests per minute per organization.
    *   Write Requests: 50 requests per minute per organization.
*   **Security Access Context Constraints:**
    *   Access Levels: Maximum 500 access levels per organization.
    *   Conditions: Maximum 40 conditions per access level.
    *   CEL (Common Expression Language) Complexity: Maximum list length of 200.
    *   VPC Networks: Maximum 500 VPC networks across all access levels per policy.

## 8. Google Workspace CLI (GWS API / Admin SDK)
*   **Execution Limitations:**
    *   Maximum 180 seconds allowed for processing any single underlying Workspace API request before triggering a timeout error.
*   **Context Payload Caps:**
    *   Recommended max payload size is 2 MB per batch/request to prevent system lag or unhandled 413 exceptions.
*   **Quotas & Automation Constraints:**
    *   Workspace Project Quotas (e.g., Sheets/Docs): 300 requests per minute per project; 60 requests per minute per user per project.
    *   Requests are applied atomically; if any sub-request in a batch fails, the entire transaction is rolled back.
