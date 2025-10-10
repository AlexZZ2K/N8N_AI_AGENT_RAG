# N8N_AI_AGENT_RAG

> **Demo:** [https://preview--alexchanrag-test.lovable.app/](https://preview--alexchanrag-test.lovable.app/)

An n8n + OpenAI + Supabase RAG Agent for intelligent document Q&A, designed by **Alex Chan (@AlexZZ2K)**.

---

## 🧭 Overview

This project implements a full **Retrieval-Augmented Generation (RAG)** workflow for intelligent question answering over structured and unstructured text sources, such as CAO documents and policy PDFs.

Built in **n8n**, the pipeline performs end-to-end ingestion, cleaning, chunking, embedding, retrieval, and AI response generation — all with automated meta-logging.

---

## ⚙️ Workflow Phases

### 1️⃣ Pre-Processing Phase
- Input: PDF or website content
- Parsing via **LlamaParser** and Markdown conversion
- Manual cleanup and post-formatting
- Output: unified Markdown text for downstream processing

### 2️⃣ Chunking & Embedding Phase
- Hierarchical chunking based on headings (#, ##, ###)
- Each chunk gets a short contextual summary via LLM
- Stored as vector embeddings in **Supabase Vector Store**
- Supports contextual retrieval (Anthropic-style)

### 3️⃣ AI Agent & Logging Phase
- User submits a query via webhook/form
- Metadata logged: language, consent, topic
- RAG Agent retrieves top chunks and forms answer
- Logs success/fallback data (human help = TRUE/FALSE)
- After 3 failed replies → escalate to human agent

---

## 🗂 Repository Contents

| Folder | Description |
|---------|-------------|
| `/n8n_workflow/` | Full JSON export of the n8n automation |
| `/docs/` | Screenshots and workflow visualizations |
| `/supabase/` | Example schema for Postgres/Supabase setup |
| `/examples/` | Example webhook payload |

---

## 🧰 Setup Instructions

```bash
# 1. Clone repo
git clone https://github.com/AlexZZ2K/N8N_AI_AGENT_RAG.git
cd N8N_AI_AGENT_RAG

# 2. Import workflow into n8n
# -> n8n Dashboard → Import Workflow → upload RAG_Alex_Chan.json

# 3. Configure credentials
# - OpenAI API Key
# - Supabase URL + Service Key
# - Postgres credentials for meta_data logging

# 4. Test via webhook or form input
```

---

## 📊 References

- [OpenAI Embeddings API](https://platform.openai.com/docs/guides/embeddings)
- [Supabase Vector Database](https://supabase.com/docs/guides/ai)
- [n8n LangChain Nodes](https://docs.n8n.io/integrations/langchain/)
- [Anthropic Contextual Retrieval](https://www.anthropic.com/news/contextual-retrieval)

---

© 2025 – Built by **Alex Chan**  
GitHub: [@AlexZZ2K](https://github.com/AlexZZ2K)