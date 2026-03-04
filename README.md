# Clara AI Automation Pipeline

## Overview

This project implements a zero-cost automation pipeline that converts demo call transcripts into Retell AI agent configurations and automatically updates them during onboarding.

The workflow was built using **n8n** and **Google Sheets** with rule-based extraction to avoid paid APIs.

---

# Architecture

Pipeline A: Demo Call → Preliminary Agent

Transcript → Account Memo JSON → Agent Spec → Storage

Pipeline B: Onboarding Update → Agent Revision

Update Input → Patch Memo → Regenerate Agent Spec → Versioned Output

---

# Tools Used

- n8n (automation orchestration)
- Google Sheets (storage layer)
- JavaScript nodes for data transformation
- Rule-based extraction logic

All tools operate on **free tiers only**.

---

# Dataset

The workflow processes:

- 5 demo call transcripts
- onboarding updates

Each account generates:

- Account Memo JSON
- Retell Agent Draft Spec

---

# Workflow

Pipeline A:

1. Load demo transcript dataset
2. Extract structured account memo
3. Generate Retell agent configuration
4. Store artifacts in Google Sheets

Pipeline B:

1. Accept onboarding update
2. Apply update to account memo
3. Regenerate agent configuration
4. Create versioned output (v1 → v2)
5. Record changelog

---

# Outputs

Generated artifacts include:

- Structured Account Memo JSON
- Retell Agent Draft Spec JSON
- Versioned updates (v1 and v2)
- Change logs

Outputs are stored in the `/outputs` directory.

---

# Running the Workflow

1. Install Docker
2. Run n8n locally
3. Import `workflows/n8n_workflow.json`
4. Load demo dataset
5. Execute the workflow

---

# Limitations

Rule-based extraction is used instead of an LLM to ensure zero-cost operation.

In production this step would be replaced with an LLM extraction pipeline.

---

# Demo

The workflow demonstrates:

- automated agent generation
- structured data extraction
- configuration versioning
- onboarding updates

---

# Future Improvements

- LLM-powered extraction
- automatic diff viewer
- dashboard for agent configuration tracking
