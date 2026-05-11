## ⚙️ Prerequisites & System Compatibility
**Operating System:** The Autopsy 4.23.0 MCP over STDIO Server is currently available for Windows environments only.
**Supported GenAI Clients:** This architecture supports clients such as Claude Desktop and LM Studio. Note that while ChatGPT Desktop is supported, it requires a Pro+ subscription to utilize MCP servers.

## ⚠️ Performance & Configuration Warnings
**EDR Whitelisting:** Endpoint Detection and Response (EDR) agents monitoring case folders and disk images have been observed to cause significant performance slowdowns. Ensure these storage locations are excluded from active EDR scans to maintain optimal ingest and query speeds.
**Incident Isolation:** To prevent the LLM from confusing context and pulling artifacts from the wrong host, it is highly recommended to only have one case or incident open at a time across Autopsy and Cyber Triage.

## 🔧 Troubleshooting Guide
**Hard Restarting Claude Desktop:** Simply closing the Claude Desktop windows does not fully shut down the application. To force the client to reload the MCP configurations, you must explicitly quit the application from the system taskbar in the lower right-hand corner.
**Tool Amnesia:** GenAI clients update rapidly and may occasionally "forget" the MCP tools; a quick restart of the client typically resolves this issue.
**Context Saturation (Too Big Errors):** If an MCP tool query returns more than 1 megabyte of data, Claude Desktop may throw a "too big" error and halt the process. If this occurs, investigators must refine their prompt to return a more focused subset of data.

## 🛡️ Privacy & Analytical Guardrails
**Data Training Opt-Outs:** If utilizing public cloud models (e.g., Anthropic's Claude) instead of local BYOAI infrastructure, ensure you are utilizing a paid tier (e.g., $20/month) to opt out of having your incident data used for future AI training. Additionally, disable thumbs up/down feedback features, as clicking these can transmit data back to the provider.
**Mandatory Verification:** Because this integration operates as a read-only overlay, the AI is acting as an analytical assistant, not an absolute authority. Human investigators must manually verify any correlations or suspicious items flagged by the LLM against the raw data within the Autopsy interface.
**Prompting Boundaries:** Avoid subjective prompts. For example, do not ask the LLM *why* a user deleted a specific file, as the AI cannot reliably infer intent and may hallucinate a narrative. Keep queries focused on deterministic data extraction and summarization.
