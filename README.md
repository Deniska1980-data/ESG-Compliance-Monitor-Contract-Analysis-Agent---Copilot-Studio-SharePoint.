ESG Compliance Monitor – Contract Analysis Agent

(Copilot Studio + SharePoint + Azure OpenAI)

Enterprise-grade AI agent built using Microsoft Copilot Studio to analyze public ESG-related contracts stored in SharePoint Online.

The agent identifies:

ESG obligations

Compliance requirements

Regulatory and contractual risks

Financial and reporting impacts

It produces structured, audit-ready summaries suitable for management, compliance teams, and internal review.
Key Characteristics

SharePoint-native knowledge access via Microsoft 365 permissions

Azure OpenAI used strictly for reasoning

Clear separation between enterprise data access and AI processing

Audit-friendly outputs with explicit source references

No legal advice

No personal data processing

Why This Project Exists

Organizations face increasing pressure to comply with CSRD / ESRS, ESG reporting obligations, and public procurement transparency.

Manual contract reviews are:

Slow

Error-prone

Difficult to audit

This project demonstrates how Copilot Studio can orchestrate Azure OpenAI safely within enterprise governance boundaries.

Architecture Overview

This solution intentionally separates AI reasoning from enterprise data access.

High-level flow:
User  
 → Copilot Studio Agent  
   → Microsoft Graph (SharePoint Knowledge)  
     → Azure OpenAI (Reasoning Only)  
       → Structured ESG Compliance Output

Key Architecture Principles

Least privilege
The agent reads only the selected SharePoint library or folder.

Governance first
Metadata-based classification and strict scope limitation.

Auditability
Every output references the source document.

Security by design
Azure OpenAI never directly connects to SharePoint.

SharePoint Structure

SharePoint Site: ESGComplianceHub
Document Library: Documents

Documents/
├─ 01_Legislation
├─ 02_ESG_Policies
├─ 03_Contracts
│   ├─ ESG_Public_Contract_Source.docx
│   ├─ ESG_Public_Contract_Source.pdf
├─ 04_Reports
├─ 05_AI_Outputs

Only documents stored in 03_Contracts are used for contract analysis.

Knowledge Connection Model
| Component               | Access                          |
| ----------------------- | ------------------------------- |
| Copilot Studio          | Microsoft 365 permissions       |
| SharePoint              | Native Graph-based access       |
| Azure OpenAI            | Receives retrieved context only |
| Standalone Azure OpenAI | ❌ No SharePoint access         |

Important:
Standalone Azure OpenAI cannot see SharePoint.
This is intentional and correct.

Agent Responsibilities

The agent performs analytical review only:

Identify ESG obligations

Identify compliance requirements

Detect missing targets, timelines, KPIs

Highlight compliance risks

Assess potential financial or reporting impacts

The agent does not:

Provide legal advice

Process personal data

Make binding compliance decisions

Example Outputs
ESG Obligations Summary

CSRD / ESRS alignment requirements

ESG reporting scope definition

Sustainability KPI responsibilities

Compliance Risks

Incomplete ESG reporting

Missed regulatory deadlines

Weak enforcement mechanisms

Financial Impact

Contractual penalties

Daily delay penalties

Reputational risk exposure

# Screenshots – Copilot Studio vs Azure OpenAI

This folder documents the practical behavior of the ESG Compliance Monitor across Microsoft Copilot Studio, SharePoint, and standalone Azure OpenAI.

## Copilot Studio – Question & Answer (Live Example)

Below is a real interaction with the ESG Compliance Monitor agent in **Microsoft Copilot Studio**.
The agent analyzes an ESG public contract stored in SharePoint and produces structured compliance risks.

![Copilot Studio – Question to AI Agent](screenshots/screenshot_Copilot_studio_question%20AI_Agent.JPG)

---
**Copilot Studio agent analyzing ESG contract stored in SharePoint**

![Copilot Studio – Question](screenshots/screenshot_Copilot_studio_question AI_Agent.JPG)

![Copilot Studio – Agent Answer](screenshots/screenshot_Copilot_studio_AI_Agent_answear.JPG)

### Copilot Studio – Identified ESG risks

![Copilot Studio – Identified Risks](screenshots/screenshot_Copilot_sstudio_Identified_risks.JPG)

### Azure OpenAI – Standalone Agent (no SharePoint access)

Standalone **Azure OpenAI** processes only the context provided by Copilot Studio.
It never connects directly to SharePoint.

![Azure OpenAI Agent](screenshots/screenshot_Azure_OpenAI_Agent_answearJPG.JPG)

## Copilot Studio – Knowledge & Analysis

### Copilot Studio – Agent question and answer
[IMAGE]

### Copilot Studio – Identified ESG risks
[IMAGE]

## Azure OpenAI (Standalone)

### Azure OpenAI – Agent response
[IMAGE]

---

## Key Observations

- Copilot Studio can **retrieve SharePoint documents automatically** using Microsoft 365 permissions.
- Standalone Azure OpenAI **cannot access SharePoint directly** and requires manual document upload or pasted text.
- This separation is intentional and aligns with enterprise security and governance requirements.

---

## Architectural note

These screenshots demonstrate that:
- Copilot Studio can directly access SharePoint via Microsoft 365 permissions
- Azure OpenAI **cannot** access SharePoint directly
- Azure OpenAI processes only the context provided by Copilot Studio or manual upload


Azure OpenAI – Standalone Agent (No SharePoint Access)

What This Repository Demonstrates

Correct enterprise use of Azure OpenAI

Secure Copilot Studio orchestration

SharePoint-based knowledge grounding

ESG-focused contract analysis

Audit-ready AI outputs

Disclaimer

This project is for educational and portfolio purposes only.

No legal advice

No personal data

Uses publicly available or mock ESG contract content

Author

Denisa Pitnerová
AI Agents · DevOps · Microsoft 365 · Azure · ESG Automation
