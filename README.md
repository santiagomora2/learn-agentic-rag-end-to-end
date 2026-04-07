# Learn Agentic RAG: From Foundations to Production

A hands-on, step-by-step learning journey for building intelligent retrieval-augmented generation (RAG) systems with agentic reasoning. Learn how to combine **Claude**, **LangGraph**, **FastAPI**, and **Opik** to build systems that think about *when* and *how* to retrieve information.

**This is a teaching project by a student, for students.** It's open source (MIT), assumes you know Python basics, and takes ~11 hours to complete.

---

## 🎯 What You'll Build

By lesson 5, you'll have:

- ✅ **A working RAG system** that retrieves from local documents using ChromaDB
- ✅ **An agentic layer** that decides *when* to retrieve and *what* tools to use
- ✅ **A production-ready API** exposing everything via FastAPI
- ✅ **Full observability** with Opik—see cost, latency, and quality in real time
- ✅ **Production patterns**—caching, error handling, cost optimization

All running locally. All open source (except Claude API, which is cheap).

---

## 📋 Prerequisites

- **Python 3.11+**
- **Familiarity with Python basics**: functions, classes, async/await concepts
- **An Anthropic API key**: [Get one free here](https://console.anthropic.com)
  - Very cheap for learning (~$0.01 per 1000 API calls typical)
- **~11 hours** over a few weeks (can't be rushed)

**Nice to have (not required):**
- Experience with FastAPI, Docker, or LLMs
- Background in ML or embeddings
- Curiosity and a willingness to experiment

---

## 🚀 Quick Start (5 minutes)

```bash
# Install uv (if you don’t have it)
pip install uv

# Clone this repo
git clone https://github.com/santiagomora2/learn-agentic-rag-end-to-end/.git
cd repo

# Create virtual environment + install dependencies (from pyproject.toml + lockfile)
uv sync

# Activate environment
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Copy the environment template
cp .env.example .env

# Add your Anthropic API key to .env
# ANTHROPIC_API_KEY=sk-ant-...

# Verify setup
python -c "import anthropic; print('✓ Ready to go')"

# Start the first lesson
cd 00-foundations
jupyter notebook 01_llm_basics.ipynb
```

If Jupyter opens in your browser, you're good!

---

## 📚 Learning Path (6 Lessons, ~11 hours)

Each lesson builds on the previous. By lesson 5, you've built a complete system. Lesson 6 adds production patterns.

### Lesson 0: Foundations
**Goal:** Understand why RAG works and what tools you're using.

📂 **Folder:** [`00-foundations/`](./00-foundations/)

**Notebooks:**
1. `01_llm_basics.ipynb` — Claude API, tokens, costs
2. `02_rag_theory.ipynb` — Why retrieval matters, the RAG loop
3. `03_vector_stores.ipynb` — ChromaDB hands-on

**What You'll Learn:**
- What embeddings are (geometrically)
- Why you can't just give Claude all your documents
- How vector databases work
- Why ChromaDB is good for learning

**Deliverable:** A working vector store with 5 sample documents.

---

### Lesson 1: Basic RAG (🚧 In Development 🚧)
**Goal:** Build a complete RAG system from scratch.

📂 **Folder:** [`01-basic-rag/`](./01-basic-rag/)

**Notebooks:**
- `simple_rag.ipynb` — Complete simple RAG implementation. Naive RAG vs. better RAG (HyDE example)

**What You'll Learn:**
- How to load documents and split them intelligently
- Building a complete end-to-end RAG
- When RAG works well, when it doesn't

**Hands-On:**
- Load 3 documents
- Query the system
- See why naive retrieval fails
- Compare with semantic retrieval

**Deliverable:** A working RAG that answers questions over documents.

---

### Lesson 2: Tools & Agents with LangGraph (🚧 In Development 🚧)
**Goal:** Understand tools and build an agentic state machine.

📂 **Folder:** [`02-tools-and-agents/`](./02-tools-and-agents/)

**Notebooks:**
- `tools_basics.ipynb` — What are tools? Why agents use them
- `langgraph_intro.ipynb` — State graphs, node execution, loops

**Code (in `src/`):**
- `tools.py` — Base Tool class + examples (Calculator, Time)
- `agent.py` — SimpleAgent that orchestrates tools
- `graphs.py` — LangGraph state machine

**What You'll Learn:**
- Tools aren't just prompts—Claude *chooses* when to use them
- State machines vs. loops
- How LangGraph makes complex workflows clean
- Tool calling, execution, error handling

**Hands-On:**
- Build an agent with 2–3 tools
- Watch it decide which tool to use
- Add a new tool without modifying agent code
- See what happens when tools fail

**Deliverable:** A working agent that uses multiple tools intelligently.

---

### Lesson 3: Agentic RAG (🚧 In Development 🚧)
**Goal:** Combine RAG + agents—retrieval becomes a tool the agent chooses to use.

📂 **Folder:** [`03-agentic-rag/`](./03-agentic-rag/)

**Notebooks:**
- `agentic_rag_notebook.ipynb` — The big "aha" moment
- `retrieval_tool_design.ipynb` — Making tools Claude likes (optional)

**Code (in `src/`):**
- Imports from lesson 1: `rag_pipeline.py`, `embedder.py`, etc.
- `retrieval_tool.py` — Wraps RAG as a tool
- `direct_answer_tool.py` — For questions Claude can answer directly
- `agentic_rag.py` — Orchestrates everything
- `response_formatting.py` — Adds citations to responses

**What You'll Learn:**
- RAG always retrieves; agents *decide* to retrieve
- Multi-step reasoning (e.g., retrieve, then reason)
- When to use knowledge vs. retrieval
- How to prevent hallucination with citations

**Hands-On:**
- Ask agent "What's 2+2?" → See it skip retrieval
- Ask "What's our parental leave policy?" → See it retrieve
- Ask compound question → See multi-step reasoning
- Add a new tool (e.g., web search) automatically

**Deliverable:** An intelligent system that knows when to retrieve.

---

### Lesson 4: FastAPI Deployment (🚧 In Development 🚧)
**Goal:** Wrap your agentic RAG in a production API.

📂 **Folder:** [`04-fastapi-deployment/`](./04-fastapi-deployment/)

**Notebooks:**
- `api_design.ipynb` — REST design, async patterns

**Code:**
- `main.py` — FastAPI app (ready to run)
- `models.py` — Pydantic request/response schemas
- `routers/` — Endpoints for chat and document management
- `dependencies.py` — Setup (DI pattern)
- `tests/` — Unit tests

**What You'll Learn:**
- REST API design (routes, schemas, errors)
- Async FastAPI for concurrent requests
- Request validation with Pydantic
- Error handling (400, 500, etc.)
- Testing your API

**Hands-On:**
- Start the API locally
- Visit http://localhost:8000/docs (auto-docs)
- Make requests via Swagger UI
- Upload new documents via POST
- See errors handled gracefully

**Deliverable:** A production-grade API serving your agentic RAG.

---

### Lesson 5: Monitoring with Opik (🚧 In Development 🚧)
**Goal:** Instrument your API to see what's happening in production.

📂 **Folder:** [`05-monitoring-with-opik/`](./05-monitoring-with-opik/)

**Notebooks:**
- `opik_setup.ipynb` — Installation, configuration
- `instrumentation.ipynb` — Adding traces

**Code:**
- `opik_config.py` — Client setup
- `instrumentation.py` — Decorators for tracing
- `docker-compose.yml` — Self-hosted Opik (PostgreSQL + server)

**What You'll Learn:**
- What observability means (vs. just logging)
- Traces: structured records of API calls
- Reading trace waterfall (where time is spent)
- Cost per request, token usage, latency
- Detecting failures and quality issues

**Hands-On:**
- Start full stack: `docker-compose up`
- Make API requests
- Visit Opik dashboard (http://localhost:3000)
- See traces come in live
- Calculate total cost of your requests
- Find slow requests, optimize them

**Deliverable:** A fully monitored system with cost + quality dashboards.

---

### Lesson 6: Production Patterns (🚧 In Development 🚧)
**Goal:** Make your system robust, cheap, and scalable.

📂 **Folder:** [`06-production-patterns/`](./06-production-patterns/)

**Notebooks:**
- `error_handling.ipynb` — Handling failures gracefully
- `caching_strategies.ipynb` — Avoid redundant retrieval
- `cost_optimization.ipynb` — Model selection, token budgets
- `scaling_and_bottlenecks.ipynb` — When to upgrade services

**Code:**
- `error_handling.py` — Custom exceptions
- `caching.py` — Retrieval caching layer
- `cost_optimizer.py` — Smart model selection
- `examples/` — Real scenarios

**What You'll Learn:**
- Error recovery (graceful degradation)
- Caching strategies (hit rates, TTLs)
- Model selection (Haiku for simple, Sonnet for complex)
- Identifying bottlenecks with Opik
- When to upgrade (ChromaDB → Pinecone, etc.)

**Hands-On:**
- Implement retrieval caching, measure cost savings
- Route simple queries to Haiku, complex to Sonnet
- Trigger intentional failures, see recovery
- Use Opik to compare optimization impacts

**Deliverable:** An optimized, production-ready system.

---

## 🏗️ Architecture Overview

```
┌─────────────────┐
│   User Input    │
└────────┬────────┘
         │
         ▼
┌──────────────────────────┐
│   FastAPI Endpoint       │  Lesson 4
│  /chat  /documents       │
└────────┬─────────────────┘
         │
         ▼
┌──────────────────────────┐
│  LangGraph Agent         │  Lessons 2–3
│  ┌──────────────────┐    │
│  │ Decide: Retrieve?│    │
│  └──────────────────┘    │
└────────┬─────────────────┘
         │
         ├─────────────┬─────────────┐
         │             │             │
         ▼             ▼             ▼
    Retrieval      Tools         Claude
    (Lesson 1)     (Lesson 2)   (Lesson 0)
    ChromaDB
         │             │             │
         └─────────────┴─────────────┘
                   │
                   ▼
         ┌─────────────────────────┐
         │  Response + Citations   │
         └────────┬────────────────┘
                  │
                  ▼
         ┌──────────────────────┐
         │  Opik Tracing        │  Lesson 5
         │  Cost, Latency, ...  │
         └──────────────────────┘
```

---

## 🛠️ Tech Stack (Why Each)

| Component | Technology | Why? | Cost |
|-----------|-----------|------|------|
| **LLM** | Claude (Anthropic) | SOTA reasoning, clear pricing | ~$0.01–$0.10 per 1K API calls |
| **Retrieval** | ChromaDB | Lightweight, no external DB, free | Free |
| **Orchestration** | LangGraph | Clean state machines, production-ready | Free |
| **API** | FastAPI | Fast, async-native, auto-docs | Free |
| **Embedding Model** | all-MiniLM-L6-v2 | Small, fast, free, good quality | Free |
| **Monitoring** | Opik | Open source, self-hosted, cost tracking | Free (self-hosted) |

---

## 📖 Frameworks We're Grateful For

This tutorial builds on incredible open-source projects:

- **[Anthropic Claude](https://anthropic.com)** — LLM backbone, reasoning engine
- **[LangGraph](https://github.com/langchain-ai/langgraph)** — Agent orchestration (MIT Licensed)
- **[ChromaDB](https://github.com/chroma-core/chroma)** — Vector database (Apache 2.0)
- **[FastAPI](https://fastapi.tiangolo.com/)** — Web framework (MIT)
- **[Opik](https://github.com/comet-ml/opik)** — LLM observability (Apache 2.0)
- **[Sentence Transformers](https://www.sbert.net/)** — Embeddings (Apache 2.0)
- **[Pydantic](https://docs.pydantic.dev/)** — Data validation (MIT)

**Thanks to all maintainers and communities.** 🙏

---

## 🤔 Common Questions

### Do I need an Anthropic API key?
Yes. It's required only for lessons 0–5. It's **very cheap** for learning:
- First 10 calls: ~$0.001
- Full learning journey: ~$5–10
- [Get free API credits here](https://console.anthropic.com)

### Can I use a different LLM?
Yes! The code in lesson 4 separates Claude from the API. Swap the provider. But Claude is excellent for reasoning—you'd learn less by switching.

### Do I need to learn all lessons in order?
**Ideally, yes.** Each lesson builds on previous knowledge. But:
- If you just want to learn RAG, stop after lesson 1
- If you want an API, start at lesson 4 (we provide lesson 1 code)
- If you just want monitoring, jump to lesson 5

### Why ChromaDB and not Pinecone/Weaviate/Vector DB X?
ChromaDB:
- ✅ Runs on your laptop (no signup needed)
- ✅ Persists to disk (not in-memory)
- ✅ Good enough for millions of vectors
- ✅ Free and open source

### How long does each lesson take?
- Lesson 0: TBD 
- Lesson 1: TBD
- Lesson 2: TBD
- Lesson 3: TBD
- Lesson 4: TBD
- Lesson 5: TBD
- Lesson 6: TBD

**Total: ~TBD hours.** But it's spread over weeks/months. Can't be rushed.

### I'm stuck. How do I get help?
1. Check the notebook markdown (there are hints)
2. Read the `README.md` in that lesson folder
3. Look at example code in `src/`
4. Open an issue on GitHub (include: Python version, error message, what you tried)

### Can I contribute?
Yes! See [CONTRIBUTING.md](./CONTRIBUTING.md). Ideas:
- Found a bug?
- Better explanation for a concept?
- New example code?
- Want to translate lessons?

All welcome.

---

## 📦 Repository Structure

```
agentic-rag-tutorial/
├── README.md                          # You are here
├── SETUP.md                           # Dev environment guide
├── CONTRIBUTING.md                    # How to contribute
│
├── 00-foundations/                    # Lesson 0: Theory
│   ├── README.md
│   ├── 01_llm_basics.ipynb
│   ├── 02_rag_theory.ipynb
│   ├── 03_vector_stores.ipynb
│   ├── example_docs/                  # Sample data
│   └── requirements.txt
│
├── 01-basic-rag/                      # Lesson 1: RAG
│   ├── README.md
│   ├── simple_rag.ipynb
│   ├── understanding_chunks.ipynb
│   ├── src/
│   │   ├── embedder.py
│   │   ├── document_loader.py
│   │   ├── chroma_store.py
│   │   ├── rag_pipeline.py
│   │   └── config.py
│   ├── example_docs/
│   └── requirements.txt
│
├── 02-tools-and-agents/               # Lesson 2: Agents
│   ├── README.md
│   ├── tools_basics.ipynb
│   ├── langgraph_intro.ipynb
│   ├── src/
│   │   ├── tools.py
│   │   ├── agent.py
│   │   ├── graphs.py
│   │   └── utils.py
│   ├── examples/
│   └── requirements.txt
│
├── 03-agentic-rag/                    # Lesson 3: RAG + Agents
│   ├── README.md
│   ├── agentic_rag_notebook.ipynb
│   ├── src/
│   │   ├── retrieval_tool.py
│   │   ├── direct_answer_tool.py
│   │   ├── agentic_rag.py
│   │   └── response_formatting.py
│   └── requirements.txt
│
├── 04-fastapi-deployment/             # Lesson 4: API
│   ├── README.md
│   ├── api_design.ipynb
│   ├── main.py
│   ├── models.py
│   ├── dependencies.py
│   ├── routers/
│   │   ├── chat.py
│   │   └── documents.py
│   ├── tests/
│   │   ├── conftest.py
│   │   ├── test_chat.py
│   │   └── test_documents.py
│   ├── requirements.txt
│   ├── Dockerfile
│   └── .env.example
│
├── 05-monitoring-with-opik/           # Lesson 5: Monitoring
│   ├── README.md
│   ├── opik_setup.ipynb
│   ├── instrumentation.ipynb
│   ├── src/
│   │   ├── opik_config.py
│   │   └── instrumentation.py
│   ├── dashboards/
│   │   └── metrics_guide.md
│   ├── requirements.txt
│   └── docker-compose.yml
│
├── 06-production-patterns/            # Lesson 6: Production
│   ├── README.md
│   ├── error_handling.ipynb
│   ├── caching_strategies.ipynb
│   ├── cost_optimization.ipynb
│   ├── scaling_and_bottlenecks.ipynb
│   ├── src/
│   │   ├── error_handling.py
│   │   ├── caching.py
│   │   ├── cost_optimizer.py
│   │   └── rate_limiter.py
│   └── examples/
│
├── .env.example                       # Environment template
├── docker-compose.yml                 # Full stack (API + Opik)
└── pyproject.toml                     # All dependencies
```

---

## 🎓 Learning by Doing

This is **not** a read-only tutorial. You're expected to:

1. **Type the code yourself** (copy-paste is fine, but type once)
2. **Break things intentionally** (see what happens)
3. **Modify examples** (change parameters, add features)
4. **Ask "why?"** before "how?" (read the notebooks, they explain)
5. **Experiment** (the best learning is through mistakes)

Each notebook has exercises. Do them. They take 30–60 minutes per lesson and are where real learning happens.

## 📝 License

MIT License. Use, modify, teach, learn—it's all yours.

---

## 🙏 Acknowledgments

Built for the next generation of AI engineers at Tecnológico de Monterrey, Guadalajara.

Special thanks to:

- **Mentors** who inspired the teaching approach
- **Open source communities** (LangGraph, Opik, ChromaDB, etc.)

---

## 🚀 Ready to Start?

Pick a lesson and open the notebook:

- **New to AI?** Start with [Lesson 0: Foundations](./00-foundations/README.md)
- **Know RAG?** Jump to [Lesson 2: Tools & Agents](./02-tools-and-agents/README.md)
- **Want an API?** Go to [Lesson 4: FastAPI](./04-fastapi-deployment/README.md)

**Questions?** [Open an issue](https://github.com/santiagomora2/learn-agentic-rag-end-to-end/issues).

**Have feedback?** [Discussions welcome](https://github.com/santiagomora2/learn-agentic-rag-end-to-end/discussions).

---

**Built with ❤️ by Santiago for learners everywhere.**

*If this helped you, please star the repo and share it with others!* ⭐