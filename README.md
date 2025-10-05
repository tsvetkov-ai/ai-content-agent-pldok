# AI Content Agent — Pldok (v4)

An AI-driven automation workflow built with **n8n**, **PostgreSQL**, **Redis**, and **LLMs** (Claude, GPT-4o, Gemini) that generates, translates, and publishes multilingual content to WordPress automatically.

**Status:** Production 🚀 | **Stack:** n8n, PostgreSQL, Redis, Claude, GPT-4o, Gemini

---

## 🌍 Overview

This system powers **[Pldok.pl](https://pldok.pl)** — a multilingual portal for migrants in Poland, providing automated content in Polish and Russian.

### Key Metrics:
- 📈 Processes **100+ articles/month** automatically
- ⏱️ Reduces manual work by **70%**
- 💰 Saves approximately **€5,000/year** in content costs
- ✅ **Zero API-limit errors** with PostgreSQL-based quota management

---

## ✨ Features

- 🔄 **End-to-End Automation**: News aggregation → Content generation → Translation → WordPress publishing
- 🧠 **LLM Orchestration**: Fallback chain (Claude → GPT-4o → Gemini) for reliability
- 💾 **State Management**: PostgreSQL tracks API usage, prevents rate limits
- 🧩 **Smart Filtering**: Levenshtein distance-based duplicate detection (95% accuracy)
- 🔔 **Real-Time Monitoring**: Telegram alerts + Redis caching for workflow health
- 🌐 **Multi-Language Ready**: Currently PL/RU, expandable to DE/AT markets

---

## 🛠️ Tech Stack

### Core:
- **n8n** — Workflow orchestration
- **PostgreSQL** — State management, logging
- **Redis** — Caching layer
- **JavaScript** — Custom fuzzy-matching and prompt logic

### AI/APIs:
- **Claude 3.5 Sonnet** (via OpenRouter) — Article generation
- **GPT-4o-mini** — Cost-effective translation
- **Gemini** — Backup generation/translation
- **SerpAPI** — News aggregation
- **WordPress REST API** — Publication
- **Telegram API** — Notifications

---

## 🏗️ Architecture

### Workflow Flow
Schedule/Webhook Trigger
↓
SerpAPI / Google Sheets (Data Sources)
↓
PostgreSQL (Filter/UPSERT duplicate check)
↓
Claude/Gemini (Content Generation)
↓
WordPress/Telegram (Publish/Notify)

### Key Components

1. **News Aggregation**
   - Fetches Google News via SerpAPI for migration topics (PESEL, ZUS, etc.)
   - Filters duplicates using JavaScript-based Levenshtein distance
   - Stores curated topics in PostgreSQL with UPSERT logic

2. **Content Generation**
   - Uses Claude 3.5 Sonnet for SEO-optimized articles (H1-H3 structure, FAQs)
   - Dynamic prompt engineering based on topic type
   - Fallback to GPT-4o/Gemini if primary model fails

3. **Translation**
   - Polish → Russian via Gemini/GPT-4o-mini
   - Preserves HTML structure and key terminology
   - Cost-optimized model selection

4. **State Management**
   - PostgreSQL tracks API quotas (SerpAPI, OpenRouter, Gemini)
   - Redis caches SerpAPI results and WordPress responses
   - JSONB logging for debugging and analytics

---

## 📊 Results

| Metric              | Impact            |
|---------------------|-------------------|
| **Cost Savings**    | €5,000/year       |
| **Manual Work**     | 70% reduction     |
| **API Reliability** | Zero rate-limit errors |
| **Duplicate Filtering** | 95% accuracy |
| **Scalability**     | Ready for DE/AT   |

---

## 🚀 Key Challenges Solved

- **API Rate Limiting**: PostgreSQL-based quota tracking across SerpAPI, OpenRouter, and Gemini eliminated all rate-limit errors.
- **Cost Optimization**: Dynamic model selection (Claude for complex generation, GPT-4o-mini for translation) reduced per-article costs.
- **Duplicate Detection**: Custom Levenshtein algorithm filters 95% of redundant topics, saving API calls.
- **Reliability**: Telegram webhooks and Redis caching ensure smooth operation and fast debugging.

---

## 📄 Documentation

Full architecture details: [AI Content Agent Architecture – Pldok v4.pdf](https://github.com/tsvetkov-ai/pldok-content-agent/blob/main/docs/AI%20Content%20Agent%20Architecture%20–%20Pldok%20v4.pdf)

---

## 🧑‍💻 About

**Denis Tsvetkov**  
AI Automation Engineer | Workflow Architect  
📍 Warsaw, Poland

Architected a production-grade AI Content Agent, delivering €5,000/year in savings. Passionate about building scalable automation solutions with n8n and LLMOps.

Open to roles in Poland, Germany (Berlin), Austria (Vienna), or remote EU.

---

## 💻 Tech Setup (High-Level)

This project's codebase is proprietary, but the architecture can be replicated:

1. **n8n**: Self-hosted or cloud instance
2. **PostgreSQL**: State management database
3. **Redis**: Caching layer
4. **API Keys**: SerpAPI, OpenRouter, WordPress, Telegram
5. **Workflow**: n8n JSON available upon request (DM for details)

---

## 🤝 Feedback & Collaboration

While the codebase is proprietary, I'm open to discussing:
- Architecture decisions and trade-offs
- LLMOps best practices
- Collaboration on similar projects

Feel free to reach out via [LinkedIn](https://www.linkedin.com/in/denis-tsvetkov-b80a95388/)!

---

## 📝 License

This documentation is available for portfolio purposes. The codebase is proprietary.

---

## 🤝 Contact

Interested in AI automation, LLMOps, or workflow design? Let's connect!  
- 💼 [LinkedIn](https://www.linkedin.com/in/denis-tsvetkov-b80a95388/)  
- 🐙 [GitHub](https://github.com/tsvetkov-ai)
- 📧 DM for collaboration or opportunities
