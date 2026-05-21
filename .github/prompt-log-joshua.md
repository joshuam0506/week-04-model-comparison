# Prompt Log — Joshua Maldonado

**Project:** AI Capstone Financial Fraud Detection System  
**Team:** Financial Fraud Detection Group  
**My Component:** AI Core / Fraud Detection Analysis  
**AI Tools Used:** ChatGPT, GitHub Copilot  

---

## How to Use This Log

This log tracks important AI interactions used during the capstone project. I will use it to show what I asked AI to help with, what result it gave me, how I evaluated it, and what I changed before using it.

This log does not include every small autocomplete or simple wording suggestion. It focuses on major AI-assisted work, such as debugging workflows, writing documentation, improving n8n expressions, and reviewing the capstone project.

---

## 2026-05-20 — Creating the Week 8 capstone project context file

**Context:**  
I was working on the Week 8 homework for prompt engineering and AI-assisted development. I needed to create a `.github/copilot-instructions.md` file for my capstone project so GitHub Copilot could better understand the financial fraud detection system.

**Prompt:**

> Help me create a copilot-instructions.md file for my financial fraud detection capstone project. The project uses Airtable, n8n, Hugging Face, Groq, Flowise, and GitHub. It detects suspicious financial transactions and updates Airtable with AI results like HF Label, HF Confidence, Groq Analysis, and AI Processed.

**Result:**  
The AI helped create a structured project context file with sections for project description, architecture, tech stack, Airtable schema, conventions, current state, repository structure, and AI assistance rules.

**Evaluation:**  
The result was useful because it gave a clear structure and included the main tools and fields used in the project. It also explained how the system works from Airtable to n8n to Hugging Face and Groq. However, I still needed to review it to make sure the field names matched the real Airtable table.

**What I changed:**  
I kept the project explanation simple and made sure the schema used fields that actually exist in the project, such as `transaction_id`, `amount`, `transaction_type`, `status`, `error_reason`, `HF Label`, `HF Confidence`, `Groq Analysis`, and `AI Processed`.

**What I learned:**  
I learned that AI gives better help when it has project context. If Copilot knows the project tools, field names, and workflow structure, it can give more accurate suggestions. I also learned that I should not copy AI output without checking it because one wrong field name can break an n8n workflow.

---

## 2026-05-20 — Auditing the capstone project before Checkpoint 2

**Context:**  
I needed to prepare for Checkpoint 2, where one record should move through all project components from start to finish without manual intervention.

**Prompt:**

> Act as a capstone project advisor. Review my financial fraud detection project and create a Checkpoint 2 readiness audit. Focus on what is working, what gaps still exist, schema issues, recommended fix order, and test data gaps.

**Result:**  
The AI created a checkpoint audit report with the status marked as “AT RISK.” It listed working parts, including Airtable, n8n, Hugging Face, Groq, and AI output updates. It also identified gaps like end-to-end testing, specialist handoff, status value consistency, and field name mismatches.

**Evaluation:**  
The audit was helpful because it showed that the biggest risk is not the AI model itself, but the handoff between components. The report was also useful because it gave specific fixes instead of vague advice.

**What I changed:**  
I reviewed the audit and kept the parts that matched the real project. I made sure the report focused on the financial fraud detection workflow and not a generic cybersecurity project.

**What I learned:**  
I learned that a working AI node is not enough for Checkpoint 2. The full project needs one clean test record that moves through ingestion, AI Core, specialist review, and integration. The main focus should be proving the end-to-end process works.

---

## 2026-05-20 — Debugging n8n and Airtable field updates

**Context:**  
While building the AI Core workflow, some Airtable fields were not updating correctly. The workflow could call Hugging Face and Groq, but not all results were showing in Airtable.

**Prompt:**

> Help me debug my n8n Update Record node. Hugging Face and Groq are working, but Airtable is not showing all the fields. I need to update HF Label, HF Confidence, Groq Analysis, and AI Processed without changing the original transaction data.

**Result:**  
The AI helped identify that the problem was in the Update Record node. Some fields were blank or mapped incorrectly. It gave corrected n8n expressions for updating only the AI output fields.

**Evaluation:**  
The help was useful because the workflow eventually updated Airtable correctly. The best part was learning that the original transaction fields should not be updated again unless necessary, because that could accidentally overwrite good data.

**What I changed:**  
I updated only the AI output fields in Airtable and kept Typecast turned on. I also adjusted the confidence score formatting so it could show 3 decimal places.

**What I learned:**  
I learned that n8n expressions must match the exact output path from previous nodes. I also learned that Airtable field formatting can affect how numbers display, even if n8n sends the correct value.
