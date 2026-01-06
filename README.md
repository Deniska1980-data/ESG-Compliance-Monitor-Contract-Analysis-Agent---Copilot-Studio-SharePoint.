# ESG Compliance Monitor – Contract Analysis Agent (Copilot Studio + SharePoint)
Enterprise-style AI agent built in **Microsoft Copilot Studio** to analyze **public ESG-related contracts** stored in **SharePoint**.  
The agent identifies **ESG obligations**, **compliance requirements**, **penalties**, and **financial/reporting risks** and produces a structured, management-ready summary.

> Scope note: The solution is intentionally designed so that **standalone Azure OpenAI does not access SharePoint directly**.  
> **Copilot Studio** orchestrates Azure OpenAI reasoning and retrieves only the necessary context from SharePoint via Microsoft 365 permissions.
---
## Why this project
Companies need fast and auditable contract reviews for ESG and compliance topics (CSRD/ESRS-related obligations, reporting deadlines, sanctions).  
This project demonstrates a safe M365-native approach:
- Controlled data access (SharePoint + permissions)
- Audit-friendly setup (library structure, metadata)
- Clear boundaries (no legal advice, no personal data processing)
---
## Architecture Overview
This solution is built using Microsoft Copilot Studio, which orchestrates Azure OpenAI reasoning while securely retrieving document context from SharePoint Online.
The architecture intentionally separates AI reasoning from enterprise data access to ensure security, governance, and auditability.

High-level flow:
- Contracts are stored in SharePoint Online.
- Copilot Studio retrieves document context using Microsoft 365 permissions.
- Azure OpenAI processes only the retrieved context, not raw SharePoint data.
- The agent produces structured ESG and compliance analysis outputs.
- Azure OpenAI never directly connects to SharePoint.
--- 
## Copilot Studio vs Standalone Azure OpenAI

This project intentionally demonstrates the difference between enterprise orchestration and standalone AI usage.

## Copilot Studio (Used in this project)

Has native integration with SharePoint
Uses Microsoft Entra ID (Azure AD) permissions
Retrieves only authorized document content
Passes limited context to Azure OpenAI
Fully compliant with enterprise security and audit requirements

## Standalone Azure OpenAI (Not used for SharePoint access)

Has no native access to SharePoint
Requires manual document upload or external ingestion pipelines
Cannot resolve SharePoint permissions
Is intentionally isolated from enterprise document storage

This separation is by design and is a key security principle.
--- 
## Data Access and Security Model

SharePoint access is controlled exclusively by Microsoft 365 permissions
Azure OpenAI never sees SharePoint URLs, metadata, or file structure
Only text content explicitly retrieved by Copilot Studio is sent to the model
No documents are stored, cached, or indexed outside SharePoint

This ensures:

Least-privilege access
Auditability
GDPR-friendly processing
Enterprise-grade data isolation

---
## SharePoint structure
SharePoint site: `ESGComplianceHub`
Document library: `Documents`
Folders:
- `01_Legislation`
- `02_ESG_Policies`
- `03_Contracts`  ← **source contracts**
- `04_Reports`
- `05_AI_Outputs`
---
## Metadata model (SharePoint columns)
Implemented custom columns for contract governance:
- **Category** (Choice): `ESG`, `Contracts`, `ESG / Contracts`
- **Source** (Text): `Public – Register of Contracts (CZ)`
- **Usage** (Choice): `AI Agent – Contract Analysis`, `Reference Only`, `Legal Source`

Recommended values for source contract files:
- Category: `ESG / Contracts`
- Source: `Public – Register of Contracts (CZ)`
- Usage: `AI Agent – Contract Analysis`
---
## Agent configuration (Copilot Studio)
Agent name: **ESG Compliance Monitor**

### System instructions (core rules)
- Analyze only documents stored in SharePoint library/folder: `Documents / 03_Contracts`
- Treat all documents as **public legal sources**
- Do **not** process personal data
- Do **not** provide legal advice
- Provide analytical summaries only
- Always reference the **source document name**
- If the document exists in SharePoint Knowledge, **never ask the user to upload/paste it**

### Knowledge source
- SharePoint → `Documents / 03_Contracts`
- Status: **Ready**
---
## Example prompts
### General analysis
- `Analyze ESG obligations and compliance risks in the document ESG_Public_Contract_Source.docx.`

### Penalties and financial exposure
- `Identify penalties, sanctions, and financial/reporting risks. Provide a management-ready summary.`

### Output format request
- `Return results as: Summary Table, Key Risks (High/Medium/Low), Missing Information, Recommendations, Source.`
---
## Output format (recommended)
1. **Summary Table** (area → key obligation → risk → evidence)
2. **Key Risks** (High / Medium / Low)
3. **Penalties & Financial Exposure**
4. **Reporting deadlines and acceptance criteria**
5. **Missing information / assumptions**
6. **Recommendations (non-legal, action-oriented)**
7. **Source document reference**
---
## GDPR & legal note
This project uses **publicly available contracts** published in the Czech Republic’s official contract register (Register of Contracts).  
No private/personal data is processed beyond what is legally public.  
This is **not legal advice**.

---
## Roadmap
- [ ] Auto-analysis workflow via Power Automate (on upload into `03_Contracts`)
- [ ] Save structured summaries into `05_AI_Outputs`
- [ ] Optional Jira integration for risk ticketing
- [ ] Risk scoring taxonomy (Low/Medium/High) + SLA rules
---
## What this demonstrates (skills)
- Microsoft Copilot Studio agent design
- M365-native governance and data access (SharePoint knowledge)
- Document classification via metadata
- Compliance-oriented prompting and safe boundaries
- Practical enterprise architecture thinking
---
## Source contract (public)
Public contract record (example):  
`https://smlouvy.gov.cz/smlouva/32375988`
