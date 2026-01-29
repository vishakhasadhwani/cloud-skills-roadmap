# Month 6: Project 1 – RAG Pipeline (Hybrid Deployment)

**Focus:** Build a RAG (Retrieval-Augmented Generation) pipeline with local + cloud components. Great portfolio project.

---

## RAG architecture

- [RAG with Ollama + Qdrant (Medium)](https://medium.com/@filipzupancic123/implement-a-simple-rag-with-ollama-qdrant-and-langchain-cc47beabc290)
- [RAG tutorial (Qdrant)](https://qdrant.tech/documentation/rag-deepseek/)
- [Local RAG API](https://otmaneboughaba.com/posts/local-rag-api/)

---

## Vector DB (self-hosted)

- [Qdrant install](https://qdrant.tech/documentation/guides/installation/)
- [Weaviate setup](https://weaviate.io/developers/weaviate/installation)
- [Qdrant Docker](https://hub.docker.com/r/qdrant/qdrant)

---

## Ollama (local LLMs)

- [Ollama](https://ollama.ai/)
- [Ollama GitHub](https://github.com/ollama/ollama)
- [Running LLMs locally with Ollama](https://www.youtube.com/watch?v=Wjrdr0NU4Sk)

---

## OpenAI API

- [OpenAI API docs](https://platform.openai.com/docs/introduction)
- [OpenAI Python](https://github.com/openai/openai-python)

---

## Deploy (e.g. Cloudflare Pages)

- [Cloudflare Pages](https://youtu.be/IXpvUD5SDzA?si=z2YM57L2xLFDEuqL)
- [Deploy to Cloudflare Pages](https://youtu.be/bNJtfFfW6tE?si=Ij4WrCJZGX43mhrQ)

---

## Repos to review

- [Ollama + Docker](https://github.com/wolffaxn/ollama-docker)
- [Project Pulse RAG](https://github.com/vmvadivel/Project-Pulse)
- [LlamaIndex](https://github.com/run-llama/llama_index) – RAG framework
- [Private RAG (Qdrant + Vultr + dspy + Ollama)](https://qdrant.tech/documentation/examples/rag-chatbot-vultr-dspy-ollama/)
- [Krish Naik](https://github.com/krishnaik06) · [Abhishek Veeramalla](https://github.com/iam-veeramalla) – MLOps/RAG projects

---

#### Project: LLM Application That Runs Anywhere

**Detailed Steps:**

1. **Install Ollama:**
   ```bash
   curl -fsSL https://ollama.com/install.sh | sh
   ```
2. **Pull a model:**
   ```bash
   ollama pull llama3.2  # or mistral, gemma
   ```
3. **Test locally:**
   ```bash
   ollama run llama3.2  # interactive chat
   ```
4. **Create Python wrapper:**
   ```python
   from langchain_community.llms import Ollama
   ```
5. **Add OpenAI fallback - Create abstraction layer:**
   ```python
   # AI helped write this abstraction
   if environment == "on-prem":
       llm = OllamaClient(local_host)
   else:
       llm = OpenAIClient(api_key)
   # Same code works everywhere
   ```
6. **Environment detection:** Automatic switching based on deployment

**⚡ Why This Matters:**

| Factor | On-Prem (Ollama) | Cloud (OpenAI) |
|--------|------------------|----------------|
| Cost | Free | $$$ per token |
| Latency | ~50ms | ~300ms |
| Data Privacy | Full control | Data leaves network |
| EU Compliance | ✅ GDPR friendly | ⚠️ Check regulations |

**GitHub Repositories:**

| Repository | Description |
|------------|-------------|
| [ollama/ollama](https://github.com/ollama/ollama) | Run LLMs locally |
| [langchain-ai/langchain](https://github.com/langchain-ai/langchain) | LLM framework |
| [localstack/localstack](https://github.com/localstack/localstack) | Local AWS cloud |

**📺 YouTube Videos:**

- Matt Williams - [Ollama Complete Tutorial](https://www.youtube.com/hashtag/ollamaai)
- LangChain Full Course - [LangChain Tutorial](https://youtu.be/vzJOAnwIokM?si=W5hsCLWs1z5zjeWs)

**Topics to Cover:**

- [ ] LLM deployment options (local vs cloud vs hybrid)
- [ ] API abstraction patterns
- [ ] Data privacy considerations (GDPR, HIPAA)
- [ ] Cost optimization strategies
---

### Project 1: RAG Pipeline (Hybrid Deployment)

**Detailed Steps:**

1. **Setup document processing:** PDF/text ingestion
2. **Choose vector database:**
   - Self-hosted: ChromaDB or Qdrant ($0/month)
   - Managed: Pinecone ($70/month)
3. **Create embeddings pipeline:**
   ```python
   from langchain.text_splitter import RecursiveCharacterTextSplitter
   from langchain.embeddings import OllamaEmbeddings
   from langchain.vectorstores import Chroma
   ```
4. **Build retrieval chain:** Query → Embed → Search → Retrieve → Generate
5. **Add hybrid LLM:** Ollama (local) + OpenAI API (fallback)
6. **Deploy frontend:** Cloudflare Pages ($0/month)
7. **Document metrics:** Response time, cost per query, accuracy

**💰 Cost Breakdown:**

| Component | Self-Hosted | Managed |
|-----------|-------------|---------|
| Vector DB | $0 | $70/month (Pinecone) |
| LLM | $0 (Ollama) | Variable (OpenAI) |
| Frontend | $0 (Cloudflare) | $0 |
| **Total** | **~$8/month** (API calls only) | **$100+/month** |

**GitHub Repositories:**

| Repository | Description |
|------------|-------------|
| [tonykipkemboi/ollama_pdf_rag](https://github.com/tonykipkemboi/ollama_pdf_rag) | Full-stack RAG demo |
| [deeepsig/rag-ollama](https://github.com/deeepsig/rag-ollama) | RAG with LangChain + Chroma |
| [jamalissa/rag-pipeline-langchain-chromadb-ollama](https://github.com/jamalissa/rag-pipeline-langchain-chromadb-ollama) | Complete RAG pipeline |
| [chroma-core/chroma](https://github.com/chroma-core/chroma) | Vector database |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Another vector DB option |

**📺 YouTube Videos:**

- Sam Witteveen - "Building a RAG Pipeline"
- Patrick Loeber - "LangChain Crash Course"

**Topics to Cover:**

- [ ] RAG architecture (retrieval, augmentation, generation)
- [ ] Embedding models and vector similarity
- [ ] Chunking strategies for different document types
- [ ] Cost optimization: self-hosted vs managed services

---

**Next:** [Month 07 – Infrastructure Monitoring](../Month_07_Infrastructure_Monitoring/)
