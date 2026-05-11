## ⚙️ Prerequisites & System Compatibility
**Operating System:** The Autopsy 4.23.0 MCP over STDIO Server is currently available for Windows environments only[cite: 225].
**Supported GenAI Clients:** This architecture supports clients such as Claude Desktop and LM Studio[cite: 912]. [cite_start]Note that while ChatGPT Desktop is supported, it requires a Pro+ subscription to utilize MCP servers[cite: 1241].

## ⚠️ Performance & Configuration Warnings
**EDR Whitelisting:** Endpoint Detection and Response (EDR) agents monitoring case folders and disk images have been observed to cause significant performance slowdowns[cite: 227, 1262]. Ensure these storage locations are excluded from active EDR scans to maintain optimal ingest and query speeds.
**Incident Isolation:** To prevent the LLM from confusing context and pulling artifacts from the wrong host, it is highly recommended to only have one case or incident open at a time across Autopsy and Cyber Triage[cite: 831, 966].

## 🔧 Troubleshooting Guide
**Hard Restarting Claude Desktop:** Simply closing the Claude Desktop windows does not fully shut down the application[cite: 929]. [cite_start]To force the client to reload the MCP configurations, you must explicitly quit the application from the system taskbar in the lower right-hand corner[cite: 931].
**Tool Amnesia:** GenAI clients update rapidly and may occasionally "forget" the MCP tools; a quick restart of the client typically resolves this issue[cite: 933].
**Context Saturation (Too Big Errors):** If an MCP tool query returns more than 1 megabyte of data, Claude Desktop may throw a "too big" error and halt the process[cite: 1141]. [cite_start]If this occurs, investigators must refine their prompt to return a more focused subset of data[cite: 1144].

## 🛡️ Privacy & Analytical Guardrails
**Data Training Opt-Outs:** If utilizing public cloud models (e.g., Anthropic's Claude) instead of local BYOAI infrastructure, ensure you are utilizing a paid tier (e.g., $20/month) to opt out of having your incident data used for future AI training[cite: 1194]. [cite_start]Additionally, disable thumbs up/down feedback features, as clicking these can transmit data back to the provider[cite: 1195].
**Mandatory Verification:** Because this integration operates as a read-only overlay[cite: 1247], the AI is acting as an analytical assistant, not an absolute authority. [cite_start]Human investigators must manually verify any correlations or suspicious items flagged by the LLM against the raw data within the Autopsy interface[cite: 1154, 1251].
**Prompting Boundaries:** Avoid subjective prompts. [cite_start]For example, do not ask the LLM *why* a user deleted a specific file, as the AI cannot reliably infer intent and may hallucinate a narrative[cite: 899]. Keep queries focused on deterministic data extraction and summarization.
