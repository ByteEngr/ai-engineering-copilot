# 🤖 AI Engineering Copilot

> An AI-powered engineering assistant that analyses logs, identifies root causes of system failures, and generates actionable insights — so your engineers spend less time debugging and more time building.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-active-brightgreen)
![Stack](https://img.shields.io/badge/stack-Python%20%7C%20LLMs%20%7C%20Vector%20DB-informational)

---

## 🎯 Problem Statement

Engineering teams waste enormous time on:
- Manually sifting through thousands of log lines during an incident
- Writing the same boilerplate infrastructure code repeatedly
- Context-switching between tools to diagnose a single failure
- Onboarding engineers who don't know the codebase or system history

**AI Engineering Copilot replaces that toil with an intelligent assistant that understands your stack.**

---

## 🔧 What It Does

```
Engineer types:  "Why did payment-service go down at 2:47am?"
                          ↓
        [ Log Ingestion Layer ]      ←  Pulls logs from CloudWatch / Datadog / files
                          ↓
        [ Embedding + Vector Search ] ←  Finds semantically relevant log chunks
                          ↓
        [ LLM Reasoning Layer ]      ←  GPT-4 / Claude analyses and explains
                          ↓
Copilot returns: "Root cause: database connection pool exhausted due to
                 spike in /checkout requests. Recommended fix: increase
                 pool size in db_config.yaml line 34. Similar incident
                 occurred 2023-11-04, resolved by same change."
```

---

## 🧩 Core Capabilities

| Feature | Description |
|---|---|
| **Log Analysis** | Feed raw logs; get human-readable incident summaries |
| **Root Cause Detection** | AI identifies the likely origin of failures with confidence score |
| **Incident Q&A** | Ask natural language questions about what happened and why |
| **Infrastructure Generation** | Describe what you need, get Terraform / K8s YAML generated |
| **Runbook Assistant** | AI-guided step-by-step resolution based on past incidents |
| **Postmortem Drafter** | Auto-generates postmortem drafts from incident timeline |

---

## 📋 Prerequisites

- Python 3.10+
- OpenAI API key or Anthropic API key
- Log source (file, CloudWatch, Datadog, or Loki)
- (Optional) Pinecone or Weaviate for persistent vector storage

---

## 🚀 Quick Start

```bash
# Clone the repo
git clone https://github.com/ByteEngr/ai-engineering-copilot.git
cd ai-engineering-copilot

# Install dependencies
pip install -r requirements.txt

# Set your API keys
cp .env.example .env
# Add your OPENAI_API_KEY or ANTHROPIC_API_KEY to .env

# Run with a log file
python copilot.py --logs /path/to/your/app.log

# Or run in interactive mode
python copilot.py --interactive
```

---

## 📁 Project Structure

```
ai-engineering-copilot/
├── src/
│   ├── copilot.py           # Main CLI entry point
│   ├── log_ingestor.py      # Log ingestion from multiple sources
│   ├── embedder.py          # Text chunking + vector embedding
│   ├── retriever.py         # Semantic search over log history
│   ├── reasoner.py          # LLM reasoning and response generation
│   └── infra_generator.py   # Terraform / K8s YAML generation
├── prompts/
│   ├── root_cause.txt       # System prompt for root cause analysis
│   ├── postmortem.txt       # Postmortem generation prompt
│   └── infra_gen.txt        # Infrastructure generation prompt
├── tests/
├── examples/
│   ├── sample_logs/         # Example log files to test with
│   └── demo.md              # Walkthrough of a sample incident
├── .env.example
└── README.md
```

---

## 💡 Example Usage

### Analyse a log file
```bash
python copilot.py --logs logs/payment-service-2024-03-15.log --query "why did the service crash?"
```

### Generate Kubernetes deployment YAML
```bash
python copilot.py --generate-infra "Deploy a Node.js app with 3 replicas, expose port 3000, add CPU limit of 500m"
```

### Interactive incident investigation
```bash
python copilot.py --interactive
> What caused the 503 errors between 02:00 and 02:47?
> Which service was the origin of the cascade?
> Draft a postmortem for this incident
```

---

## 📊 Impact

| Metric | Traditional | With Copilot |
|---|---|---|
| Time to identify root cause | 30–90 min | 2–5 min |
| Postmortem write time | 2–4 hrs | 15 min |
| Infra boilerplate time | 1–3 hrs | 5 min |
| Junior engineer ramp-up | Weeks | Days |

---

## 🗺️ Roadmap

- [x] Log file ingestion + LLM analysis
- [x] Root cause explanation
- [x] Infrastructure YAML generation
- [ ] Slack bot integration (ask questions in Slack)
- [ ] Auto-sync with PagerDuty incidents
- [ ] Fine-tuned model on DevOps-specific data
- [ ] Web UI dashboard

---

## 🤝 Contributing

```bash
git checkout -b feature/your-feature
git commit -m "feat: your change"
git push origin feature/your-feature
# Open a Pull Request
```

---

## 📄 License

MIT © [Goziechukwu Chima-Duru](https://github.com/ByteEngr)

