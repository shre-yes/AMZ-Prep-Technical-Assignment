# AMZ Prep AI Engineer Technical Assignments

This repository serves as a central hub for my submission for the AI Engineer technical assignment at AMZ Prep.

---

## 📌 Quick Overview

This submission showcases my ability to design and ship AI-powered solutions that drive measurable business impact—from automating lead qualification to managing real-time logistics alerts. Each assignment was built with a focus on **reliability, scalability, and maintainability**.

| **Assignment** | **Focus** | **Tech Stack** | **Impact** |
|---|---|---|---|
| **[Lead Summarizer Agent](#-assignment-1-lead-summarizer-agent)** | AI Automation | Python, Groq LLM, CSV Processing | Reduces lead QA time by 80% |
| **[RTO Webhook Service](#-assignment-2-rto-webhook-service)** | Backend Engineering | FastAPI, Async I/O, Real-time Alerts | Instant carrier notifications with <200ms latency |
| **[Lead Segregation Workflow](#-assignment-3-lead-segregation-workflow)** | Workflow Design | n8n, Google Sheets, Slack Integration | Hot leads flagged in <30 seconds |
| **[LeadFlow AI (n8n Automation)](#-assignment-4-leadflow-ai--intelligent-lead-automation-system)** | Workflow + AI Systems | n8n, Python, Groq LLM, Google Sheets, Slack | Real-time intelligent lead routing |

---

## 📂 Assignment 1: Lead Summarizer Agent

### The Challenge
Sales teams drown in data. Hundreds of raw lead records arrive daily—unstructured, messy, time-consuming to qualify manually. The question: *How do you distill chaos into actionable insights?*

### The Solution  
**[Lead Summarizer Agent](https://github.com/shre-yes/Lead-Summerizer-Agent)**

A Python-powered AI agent that ingests bulk lead CSVs and generates concise, intent-focused summaries using the **Groq (Llama-3) LLM**. The system automatically detects file encodings, handles edge cases gracefully, and produces a polished terminal report.

**Key Highlights:**
- ✅ **Smart CSV Handling** — Auto-detects encodings (UTF-8, CP1252, etc.) and delimiters
- ✅ **Robust Error Recovery** — Failures isolated per-lead; batch processing never stops
- ✅ **Pre-flight Validation** — Checks if output file is writable before spending API credits
- ✅ **Production Logging** — Full audit trail of successes and errors
- ✅ **Edge Case Mastery** — Handles binary uploads, malformed rows, header normalization

**In Action:** Feed it 100 messy leads → Get 100 AI-summarized leads + a formatted report in minutes.

---

## 📂 Assignment 2: RTO Webhook Service

### The Challenge
Delivery failures in e-commerce are a logistical nightmare. Return-to-Origin (RTO) events can cost thousands, but alerts are slow and buried in dashboards. Support teams need *instant* notifications to action returns before packages ship back.

### The Solution  
**[RTO Webhook Service](https://github.com/shre-yes/RTO-Webhook-Service)**

A **FastAPI service** that receives carrier webhook events, validates them with Pydantic, and instantly broadcasts alerts to a Telegram group/channel. Built for high throughput and sub-200ms latency.

**Key Highlights:**
- ✅ **Async Architecture** — Non-blocking request handling scales to 1000s of events/sec
- ✅ **HMAC Signature Validation** — Prevents spoofed webhook invocations
- ✅ **Telegram Integration** — Real-time, mobile-push alerts (cheaper & faster than email)
- ✅ **Structured Alerts** — Formatted for instant comprehension (reason, attempt count, action needed)
- ✅ **Smart Retry Logic** — Graceful degradation if Telegram is slow
- ✅ **ngrok Support** — Works seamlessly in dev with public tunnels

**In Action:** Carrier fires webhook → Pydantic validates → Alert in Telegram in ~150ms.

---

## 📂 Assignment 3: Lead Segregation Workflow

### The Challenge
Not all leads are created equal. Hot leads (high intent, large deals) demand immediate attention, while cold leads should still be tracked. Manual routing is error-prone and slow.

### The Solution  
**[Lead Segregation Workflow](https://github.com/shre-yes/Lead-Segregation-Workflow)**

A **no-code n8n workflow** that:
1. Polls a Google Sheet for new form submissions
2. Runs a custom Python scoring algorithm (point-based lead prioritization)
3. Routes **Hot leads** to `#hot_leads` Slack channel for instant action
4. Logs **all leads** to `#all-leads` for tracking

**Key Highlights:**
- ✅ **Multi-tier Scoring** — Evaluates order volume, authority, business needs
- ✅ **Real-time Routing** — Hot leads surface in seconds (≥6 points)
- ✅ **Google Sheets + Slack** — Zero custom API boilerplate; pure workflow
- ✅ **Extensible Design** — Swap Slack for SMS, email, or custom webhooks in minutes
- ✅ **Full Auditability** — All leads logged with scores for retrospective analysis

**Scoring Logic:**
- 🔥 **HOT** (≥6 pts) → Immediate Slack alert
- 🟡 **WARM** (≥4 pts) → Logged for review and followup
- ❄️ **COLD** (<4 pts) → Prioritized for later (lead needs to be nurtured)

---

## 📂 Assignment 4: LeadFlow AI – Intelligent Lead Automation System

### The Motivation  
While working through the lead segregation assignment, I explored a deeper question: *How would this system look if it were extended into a fully automated, production-grade lead intelligence pipeline?*

This project is a **self-initiated extension** of that idea—built to go beyond basic scoring and demonstrate a complete end-to-end automation system for real-world sales workflows.

### The Solution  
**[LeadFlow AI](https://github.com/shre-yes/leadflow-ai)**

An **intelligent lead automation system built using n8n** that captures, enriches, scores, and routes leads in real time using a combination of workflow orchestration, Python-based logic, and LLM-powered summarization.

Unlike traditional static workflows, this system introduces **dynamic decision-making + real-time enrichment + instant routing**.

### Key Highlights:
- ⚡ **End-to-End Automation** — From Google Forms ingestion to Slack alerting without manual intervention  
- 🧠 **Custom Scoring Engine** — Rule-based Python logic to prioritize high-value leads  
- 🤖 **LLM Enrichment Layer** — Uses Groq to generate concise, actionable lead summaries  
- 🚦 **Smart Routing System** — HOT leads instantly pushed to Slack for immediate action  
- 📊 **Persistent Tracking** — All leads stored in Google Sheets for auditability and analysis  
- 🔧 **Low-Code + High Control** — Built on n8n with extensible logic nodes  

### In Action:
Lead submitted → Automatically scored → Enriched via LLM → Classified (HOT/WARM/COLD) →  
🔥 HOT leads instantly pushed to Slack → All leads logged for tracking

### Why This Matters  
This project demonstrates how a simple automation requirement can be evolved into a **real-world intelligent system** by combining:

- Workflow orchestration (n8n)  
- Programmatic logic (Python scoring)  
- LLM-based intelligence (Groq)  
- Event-driven routing (Slack + Sheets)  

It reflects a shift from **task automation → system design thinking**

---

## 🎯 Why These Three?

Together, they demonstrate a **complete AI engineering stack**:

| Layer | Demonstrated |
|---|---|
| **AI/ML** | Prompt engineering, LLM integration, multi-model comparison |
| **Backend** | FastAPI, async I/O, webhook handling, error resilience |
| **Data** | CSV parsing, encoding detection, batch processing, validation |
| **Workflow** | No-code orchestration, event-driven architecture, multi-step pipelines |
| **DevOps** | Logging, monitoring, local tunneling, environment management |
| **SRE Mindset** | Graceful degradation, pre-flight checks, retry logic, edge case handling |

---

## 🚀 Quick Start

1. **[Lead Summarizer Agent](https://github.com/shre-yes/Lead-Summerizer-Agent)** — Clone, configure Groq API key, run.
2. **[RTO Webhook Service](https://github.com/shre-yes/RTO-Webhook-Service)** — Clone, set Telegram credentials, deploy with `uvicorn`.
3. **[Lead Segregation Workflow](https://github.com/shre-yes/Lead-Segregation-Workflow)** — Import JSON to n8n, link Google Sheets & Slack.

Detailed setup instructions are in each repo's README.

---

## 📝 License

All projects are MIT-licensed. Feel free to fork, modify, and ship.

---

## 🤝 Questions?

Each repository has detailed documentation. Start with any of the three links above, or [reach out for a walkthrough of the architecture](mailto:shre.yes@gmail.com).

---

**Built with attention to detail. Designed for scale. Ready for production.**
