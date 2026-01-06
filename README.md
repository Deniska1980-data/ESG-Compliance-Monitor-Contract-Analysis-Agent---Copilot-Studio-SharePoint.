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

# Screenshots – ESG Compliance Monitor

This folder contains screenshots demonstrating the functionality and architecture of the ESG Compliance Monitor project.

## Copilot Studio + SharePoint

### SharePoint document library
![SharePoint ESG Compliance Hub](screenshot_SharePoint_ESG_Compliance_Hub.JPG)

### Contracts stored in SharePoint
![SharePoint Documents](screenshot_SharePoint_Documents.JPG)

### Copilot Studio – referenced sources
![Copilot Studio Knowledge Sources](screenshot_Copilot_studio_ESG_Publics_Contract_Sourse.JPG)

### Copilot Studio – identified risks
![Copilot Studio Identified Risks](screenshot_Copilot_sstudio_Identified_risks.JPG)

### Copilot Studio – agent answer
![Copilot Studio Agent Answer](screenshot_Copilot_studio_AI_Agent_answear.JPG)

---

## Azure OpenAI (standalone)

### Azure OpenAI agent playground
![Azure OpenAI Agents](screenshot_Azure_OpenAI_Agents.JPG)

### Azure OpenAI response (manual document upload required)
![Azure OpenAI Agent Answer](screenshot_Azure_OpenAI_Agent_answearJPG.JPG)

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
