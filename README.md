# DFIR Alert Triage Automation via MCP and Local LLMs

![Project Status](https://img.shields.io/badge/Status-Active-success)
![Framework](https://img.shields.io/badge/Framework-Model_Context_Protocol_(MCP)-blue)
![Tools](https://img.shields.io/badge/Tools-Autopsy_%7C_Cyber_Triage-orange)

## 📌 Executive Summary
This project demonstrates the integration of Generative AI into Digital Forensics and Incident Response (DFIR) workflows using the **Model Context Protocol (MCP)**. By connecting local, air-gapped Large Language Models (LLMs) to Autopsy and Cyber Triage forensic databases, this architecture enables automated evidence enrichment and timeline summarization while maintaining strict data privacy and read-only evidentiary boundaries.

## 🎯 Business Value & Operational Impact
* **Data Privacy (BYOAI):** Utilizing local models ensures sensitive incident data never leaves the organizational perimeter, satisfying strict GRC and regulatory compliance requirements.
* **Evidentiary Integrity:** The MCP server enforces a read-only boundary. The AI acts as an analytical overlay and cannot modify or corrupt the underlying forensic database.
* **Triage Efficiency:** Reduces analyst cognitive load by rapidly summarizing complex web history, active network connections, and system artifacts into actionable executive timelines.

## 🏗️ Technical Architecture
The integration relies on a middleman architecture where the GenAI Client (e.g., Claude Desktop or LM Studio) brokers requests between the LLM and the forensic database.

```mermaid
graph LR
    A[Local LLM / Claude Desktop] <-->|Model Context Protocol| B(Autopsy / Cyber Triage MCP Server)
    B <-->|Read-Only Queries| C[(Forensic Database)]
    A -->|Summaries & Enrichment| D[DFIR Analyst]
