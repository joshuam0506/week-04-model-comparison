# Capstone Project Context

## Project

- **Name:** AI Capstone Financial Fraud Detection System
- **Team:** Group project for AI integration course
- **What it does:** This project detects possible financial fraud by collecting transaction records, analyzing them with AI models, and updating Airtable with risk labels, confidence scores, anomaly reasons, and investigation recommendations. The system helps users or investigators identify suspicious transactions faster while still allowing human review.
- **Project type:** Financial Fraud Detection / Fraud Investigation System

## Architecture

- **Ingestion:** Transaction records are stored in Airtable. Records include transaction ID, sender ID, recipient ID, amount, transaction type, status, description, and error reason.
- **AI Core:** n8n workflows send transaction data to Hugging Face and Groq. Hugging Face provides classification or confidence scores, and Groq provides a plain-language fraud analysis.
- **Specialist:** Suspicious or high-risk records can be reviewed for possible fraud patterns, including account takeover, high-value transfers, unusual transaction types, repeated errors, or suspicious sender/recipient behavior.
- **Integration:** Airtable is the shared database. n8n reads records from Airtable, sends them to AI models, and writes results back into Airtable fields such as HF Label, HF Confidence, Groq Analysis, and AI Processed.

## Tech Stack

- n8n Cloud for workflow automation
- Airtable for the transaction database
- Hugging Face Inference API for AI model classification
- Groq API for LLM fraud analysis
- Flowise Cloud for LLM chains and RAG chatbot prototypes
- GitHub for documentation and project files
- GitHub Copilot for AI-assisted development

## Airtable Schema

### Transactions

| Field | Type | Written By | Notes |
|---|---|---|---|
| transaction_id | single line text | Ingestion | Unique transaction ID such as TXN-0001 |
| timestamp | date/time | Ingestion | Date and time of transaction |
| sender_id | single line text | Ingestion | User or account sending money |
| recipient_id | single line text | Ingestion | User or account receiving money |
| amount | number/currency | Ingestion | Transaction amount |
| transaction_type | single select/text | Ingestion | transfer, withdrawal, deposit, purchase |
| description | long text | Ingestion | Human-readable transaction description |
| status | single select/text | Ingestion / AI Core | pending, analyzed, case_created, error |
| error_reason | long text | Ingestion / AI Core | Explains invalid or unusual records |
| HF Label | single line text | AI Core | Hugging Face classification label |
| HF Confidence | number | AI Core | Hugging Face confidence score |
| Groq Analysis | long text | AI Core | Groq explanation of fraud risk |
| AI Processed | checkbox/text | AI Core | Shows whether the AI workflow processed the record |

### Investigation_Cases

| Field | Type | Written By | Notes |
|---|---|---|---|
| case_id | single line text | Specialist | Unique case ID |
| transaction_id | linked/text | AI Core / Specialist | Related suspicious transaction |
| risk_level | single select/text | AI Core / Specialist | low, medium, high, critical |
| case_status | single select/text | Specialist | open, under_review, closed |
| investigation_notes | long text | Specialist | Notes from review process |

## Conventions

- Field names should use snake_case when possible.
- Status values should be lowercase.
- Date fields should end in `_at` when created manually.
- Boolean fields should use clear names like `AI Processed` or `is_processed`.
- AI output fields should not overwrite original transaction data.
- The system should support human review and should not automatically accuse a customer of fraud.

## Current State

- **What's working:** Airtable transaction table exists. n8n can read records from Airtable. Hugging Face and Groq API calls have been tested. n8n can update Airtable with AI output fields.
- **What's in progress:** Improving workflow reliability, documentation, GitHub organization, and Flowise LLM/RAG prototypes.
- **Known issues:** Some tools can be difficult to configure on mobile. Flowise node connections may be easier on a laptop or desktop. Field name mismatches can break n8n expressions.
- **Next milestone:** Checkpoint 2 — one complete record should flow through all components end-to-end without manual intervention.

## Repository Structure

```text
ai-capstone-financial-fraud-detection-system/
  README.md
  docs/
    checkpoint2-audit.md
  .github/
    copilot-instructions.md
  workflows/
    n8n-workflow.json
  data/
    sample-transactions.csv
  components/
    ai-core/
      README.md
