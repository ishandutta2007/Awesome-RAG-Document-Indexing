# Awesome-RAG-Document-Indexing

# Top RAG & Document Indexing Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Structure-Aware Retrieval, Reasoning-Based Navigation & Enterprise Search*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **RAG & Document Indexing**. These tools help AI systems find the right information inside large document collections — from traditional vector similarity search to emerging structure-aware and reasoning-based approaches that navigate documents the way a human expert would.

**Examples** include PageIndex, Glean, Coveo, Sinequa, Lucidworks Fusion, Elastic Enterprise Search, Algolia, Amazon Kendra, AlphaSense, and Hebbia (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, structure-aware retrieval, and transparent indexing — ideal for teams prioritizing explainability, avoiding opaque "vibe retrieval," and building document intelligence they can audit and control.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Glean](https://www.glean.com/)**  
  **Enterprise search and knowledge discovery platform powered by AI.** Connects to 100+ workplace applications (Slack, Google Drive, Confluence, Jira, Salesforce) to build a unified index of company knowledge. Uses LLM-powered relevance and personalization to surface the right documents, messages, and experts. **Best for enterprises wanting turnkey search across fragmented SaaS tools** without building connectors themselves.

- **[Coveo](https://www.coveo.com/)**  
  **AI-powered enterprise search and relevance platform** for customer service, workplace, and commerce use cases. Strong connectors for Salesforce, ServiceNow, SharePoint, and legacy systems. **Best for large enterprises** needing unified search across heterogeneous systems with relevance tuning.

- **[Sinequa](https://www.sinequa.com/)**  
  **Enterprise search and intelligence platform** with 200+ connectors, natural language processing, and AI-powered relevance. **Best for regulated industries** requiring on-premise deployment and deep content analytics.

- **[Lucidworks Fusion](https://lucidworks.com/)**  
  **Enterprise search platform built on Apache Solr** with AI-powered relevance, connectors, and a visual query pipeline designer. **Best for organizations wanting Solr's power with enterprise tooling and support**.

- **[Elastic Enterprise Search](https://www.elastic.co/enterprise-search)**  
  **Hosted enterprise search from Elastic** with connectors for content sources, a web crawler, and relevance tuning UI. Integrates with Elasticsearch's vector and hybrid search capabilities. **Best for teams already on the Elastic stack.**

- **[Algolia](https://www.algolia.com/)**  
  **Developer-favorite hosted search API** with instant search, typo tolerance, and relevance out of the box. **Record-based pricing** scales steeply with catalog size. **Best for site search and e-commerce discovery** where fastest time-to-value matters.

- **[Amazon Kendra](https://aws.amazon.com/kendra/)**  
  **AWS-managed intelligent enterprise search** with natural language queries and connectors to S3, SharePoint, Salesforce, and databases. **Best for AWS-native organizations** wanting managed search without infrastructure.

- **[AlphaSense](https://www.alpha-sense.com/)**  
  **AI-powered market intelligence and document search platform** for financial professionals. Indexes SEC filings, earnings calls, broker research, and news. **Best for investment research and competitive intelligence** on professional documents.

- **[Hebbia](https://www.hebbia.com/)**  
  **AI-powered document analysis platform** for financial and legal professionals. Uses LLM reasoning over document collections to answer complex questions with citations. **Best for high-stakes document review** where traceability matters.

## Open-Source GitHub Projects

- **[PageIndex](https://github.com/VectifyAI/PageIndex)**  
  **The leading open-source vectorless, reasoning-based RAG engine** — Apache 2.0 licensed. **Replaces the vector index with a hierarchical tree index** and lets an LLM **reason** its way through it, the way a human expert turns to the right section of a long report . **The core insight**: **similarity ≠ relevance** — vector search returns what is semantically similar but not necessarily relevant; relevance requires reasoning . **Two-step retrieval**: (1) **Index** — generate a tree-structure index from document layout, (2) **Retrieve** — agentically search that tree with LLM reasoning . **No vector DBs, no chunking** — documents are organized into natural sections, not artificial chunks . **Traceable and explainable** — retrieval is based on reasoning with page and section references, not opaque "vibe retrieval" . **Benchmarks**: achieved **state-of-the-art 98.7% accuracy on FinanceBench**, demonstrating superior performance over vector-based RAG for professional document analysis . **Cost**: building a tree locally runs **about $0.001 per page** with a basic index model; a 1,000-page textbook costs a little over a dollar and a few minutes, once, and every later question reuses it . **Deployment**: self-hosted via `pip install -U pageindex` with local mode (index, retrieve, and chat entirely on your machine with your own LLM key) or PageIndex Cloud with an API key . **Best for financial reports, legal documents, regulatory filings, technical manuals, medical literature, and academic textbooks** — any long, complex professional document where traceability and context-aware retrieval matter more than raw similarity .

- **[Verity RAG](https://pypi.org/project/verity-rag/)**  
  **Open-source RAG agent with hybrid search, cross-encoder reranking, and a web dashboard** — Python-based . **BM25 keyword search + vector fusion (RRF)** for hybrid retrieval . **Cross-encoder reranking** using Sentence Transformers for relevance scoring . **ARQ task queue** for background processing with retry and backoff . **SSE status streaming** for real-time ingestion progress . **Pluggable connectors** for local filesystem (ready) and S3/Google Drive (pluggable) . **Deduplication** via content hash and source path matching . **Web dashboard** with document upload, collections, and search with score visualization . **Containerized deployment** with Postgres, Valkey, and Milvus . **Best for teams wanting a complete, self-hosted RAG pipeline with hybrid retrieval and reranking** out of the box.

- **[Ragora](https://pypi.org/project/ragora/)**  
  **Privacy-first RAG framework with specialized LaTeX and email document processing** — Python-based . **Native LaTeX parsing with citation handling** and email support . **Clean three-layer architecture** (DatabaseManager → VectorStore → Retriever) for maintainability . **Flexible search modes**: vector (semantic), keyword (exact), and hybrid with configurable alpha weighting . **Composable components** — use high-level APIs or build custom pipelines with low-level components . **Runs completely local** with sentence-transformers and Weaviate . **Best for academic research and technical documentation** where LaTeX papers and structured formats are central.

- **[PKMRAG](https://pypi.org/project/pkmrag/)**  
  **Embedded, local-first hybrid GraphRAG retrieval engine and MCP server** — Python-based . **Combines dense semantic similarity (BAAI/bge-small-en-v1.5), Tantivy BM25 keyword matching, and Reciprocal Rank Fusion** . **Graph-boosted retrieval** via `--near` anchor notes . **Semantic gap discovery** — detects unlinked note pairs with high semantic similarity (≥0.80) and infers relationships, stored separately with confidence and rationale . **MCP server** for AI agents (Claude Code, Cursor, OpenCode) without exposing raw filesystem mutation risks . **Scientific quality gating** with zero-cost IR metrics (MRR, Context Recall@5) guarding against semantic regressions . **Best for personal knowledge management (PKM) and local-first document retrieval** with graph-aware hybrid search.

- **[cairnsearch](https://www.sciencedirect.com/science/article/pii/S2352711026002347)**  
  **Privacy-first hybrid search and local RAG system for personal document collections** — open-source, academic-published . **Combines BM25 and vector search with a 0.7/0.3 weighting** for optimal top-5 relevance . **Cross-encoder reranking** rescores combined top-k candidates before truncation . **Local LLM generation** via Ollama (default llama3.1:8b) with explicit document-name delimiters and a system prompt that answers only from provided context . **PII detection** for twelve classes of sensitive data (SSN, credit card, email, phone, address, date of birth, passport, driver's licence, bank account, IP, name, medical record) . **Audit logging** for all indexing and RAG operations . **No external network calls** — extraction, embedding, retrieval, and generation all run locally . **Benchmarked on MacBook Pro M4 with 16 GB RAM** . **Best for legal and compliance document review** where privacy and auditability are non-negotiable.

- **[Meilisearch](https://github.com/meilisearch/meilisearch)**  
  **Lightning-fast, typo-tolerant search engine with hybrid semantic search and agentic retrieval** — MIT licensed, Rust-based . **Sub-50ms instant search** with built-in typo tolerance, synonyms, faceting, and tenant tokens . **AI-native**: hybrid semantic search, built-in vector storage, and **agentic retrieval for RAG** . **Model-agnostic embeddings** — connect OpenAI, Hugging Face, or Ollama through REST embedders and swap as the ecosystem evolves . **Open-source and self-hostable**, with Meilisearch Cloud starting at $20/month . **Best for developer-facing site search and AI applications** wanting fast, relevant retrieval without the complexity of Elasticsearch .

### Additional Strong Open-Source Options

- **DocForge** — Open-source tool for building versioned, RAG-ready knowledge bases from official software documentation, with zero-config discovery for PostgreSQL, MySQL, FastAPI, Kubernetes, and more . Apache 2.0 licensed .
- **Vectorless RAG (TypeScript implementation)** — A TypeScript port of the PageIndex algorithm for CSV-structured documentation, exposing a REST API with `/load` and `/query` endpoints . Demonstrates the PageIndex approach outside Python .
- **semantic-search (Go)** — Go library composing embedder, metadata store, vector store, and retrieval strategies with SQLite or PostgreSQL+pgvector backends . Supports multiple embedding models including Gemma, Nomic, E5, BGE, Qwen, and Mxbai .
- **RAGFlow** — Open-source RAG engine with deep document understanding, layout-aware DeepDoc parsing, hybrid retrieval, and citation-backed answers. Apache 2.0 licensed.

**Frameworks for building custom systems**: Combine **PageIndex** for structure-aware reasoning-based retrieval over long professional documents with traceable citations, **Verity RAG** for a complete self-hosted pipeline with hybrid search and reranking, **Ragora** for LaTeX and email document processing, **PKMRAG** or **cairnsearch** for privacy-first local RAG with graph-aware or hybrid search, and **Meilisearch** for fast typo-tolerant site search with hybrid semantic retrieval — to build a document indexing layer tailored to your document complexity, traceability requirements, and deployment constraints.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- RAG and document indexing tools differ significantly in retrieval approach, explainability, and infrastructure requirements. **PageIndex replaces vector similarity with reasoning over a tree index** — achieving 98.7% on FinanceBench while producing traceable, explainable retrieval that returns page and section references . **Vector search returns what is semantically similar but not necessarily relevant** — the core problem PageIndex addresses . **PageIndex indexing costs about $0.001 per page** with a basic model, and the tree is built once and reused . **cairnsearch runs entirely locally with no external network calls** and includes PII detection for twelve sensitive data classes . **Meilisearch is optimized for instant search and AI-native retrieval** rather than log analytics . **Traceability varies**: reasoning-based retrieval returns explicit references; vector retrieval returns opaque similarity scores.
- Self-hosted open-source solutions require proper document parsing configuration, embedding model selection (or LLM reasoning model for PageIndex), and retrieval quality evaluation against your specific document corpus.

---

**Made for AI engineers, RAG developers, and teams building document intelligence and retrieval systems.**
Let's make RAG and document indexing more open, traceable, and structure-aware.
