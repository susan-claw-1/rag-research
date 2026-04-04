# RAG & Knowledge Graph Learning Plan

A structured learning path for building a reliable pipeline that processes files into a knowledge base/graph, paired with an LLM for deep technical Q&A.

---

## Phase 1 — Foundations

### Concepts
- [ ] Understand the full RAG pipeline: Files → Parse → Chunk → Embed → Index → Retrieve → Rerank → LLM → Answer
- [ ] Read about vector similarity search (cosine similarity, approximate nearest neighbours)
- [ ] Understand the difference between keyword search (BM25) and semantic search (embeddings)
- [ ] Learn why hybrid search (keyword + semantic) outperforms either alone

### Parsing & Ingestion
- [ ] Explore document parsing libraries: `unstructured`, `docling`, `pymupdf4llm`, `markitdown`
- [ ] Understand the challenges of parsing PDFs, Word docs, HTML, and code files
- [ ] Experiment with parsing a few real files and inspecting the output quality

### Chunking
- [ ] Implement naive fixed-size chunking with overlap
- [ ] Understand semantic chunking (split on topic boundaries via embedding similarity)
- [ ] Understand structural chunking (respect headings, sections, code blocks)
- [ ] Read: Anthropic's "Contextual Retrieval" blog post (contextual chunking — prepend summaries to chunks)
- [ ] Experiment with different chunk sizes and observe impact on retrieval quality

### Embeddings
- [ ] Understand what embedding models do and how they represent text as vectors
- [ ] Compare open-source models: `nomic-embed-text`, `bge-large`, `GTE-Qwen2`
- [ ] Compare API models: OpenAI `text-embedding-3-large`, Cohere `embed-v4`, Voyage AI
- [ ] Understand dimensionality trade-offs (accuracy vs storage/compute)
- [ ] Learn about HyDE (Hypothetical Document Embeddings) — generating synthetic questions per chunk

---

## Phase 2 — Building the Retrieval Layer

### Vector Stores & Indexing
- [ ] Explore local-first options: ChromaDB, LanceDB, Qdrant (embedded mode), FAISS
- [ ] Understand how hybrid search works in LanceDB / Qdrant
- [ ] Build a small index: embed a folder of files, store in a vector DB, run queries
- [ ] Implement incremental indexing (content hashing to avoid reprocessing unchanged files)

### Retrieval Strategies
- [ ] Implement basic top-k vector similarity retrieval
- [ ] Add a reranker: cross-encoder models (`bge-reranker-v2`, `jina-reranker-v2`, Cohere Rerank)
- [ ] Implement multi-query retrieval (LLM rephrases question multiple ways, merge results)
- [ ] Experiment with retrieval parameters: top-k size, similarity thresholds, chunk overlap

### Evaluation
- [ ] Read the RAGAS docs (RAG evaluation framework)
- [ ] Build a small test set: questions with known answers from your files
- [ ] Measure retrieval precision and answer quality
- [ ] Compare: no reranker vs reranker, single query vs multi-query, different chunk sizes

---

## Phase 3 — The LLM Layer

### Prompt Engineering for RAG
- [ ] Design prompts that incorporate retrieved context effectively
- [ ] Implement source citation (model references which chunks it used)
- [ ] Handle context window management (don't just stuff everything in)
- [ ] Experiment with different models and context window sizes

### Agentic RAG
- [ ] Understand agentic RAG: LLM decides what to retrieve, iterates, asks follow-up queries
- [ ] Implement a simple agent loop: query → retrieve → evaluate → re-query if needed
- [ ] Handle query routing: simple lookups vs complex multi-step questions

---

## Phase 4 — Knowledge Graphs

### Concepts
- [ ] Understand knowledge graphs: nodes (entities), edges (relationships), properties
- [ ] Read: Microsoft's GraphRAG paper ("From Local to Global")
- [ ] Understand entity extraction from text using LLMs
- [ ] Learn about community detection and hierarchical summarisation

### Implementation
- [ ] Explore graph tools: Neo4j, NetworkX, Microsoft GraphRAG repo
- [ ] Build a small graph: extract entities and relationships from a set of documents
- [ ] Implement community summaries (GraphRAG-style) for high-level questions
- [ ] Combine graph retrieval with vector retrieval (hybrid: graph for multi-hop, vectors for lookup)

### Advanced
- [ ] Query routing: classify question complexity, route to flat RAG vs graph RAG
- [ ] Handle conflicting information across documents (timestamps, source authority)
- [ ] Multi-hop reasoning: connecting information across multiple files/entities
- [ ] Explore ontology design: what entity types and relationship types matter for your domain

---

## Phase 5 — Production Concerns

- [ ] File watching and incremental updates (detect changed/new/deleted files)
- [ ] Handle large file collections efficiently (batch processing, parallelism)
- [ ] Persistence and backup of index + graph
- [ ] Privacy and security: local-first, optional encryption
- [ ] Build a usable interface: CLI, API, or chat-based
- [ ] Cost management: embedding and LLM API costs at scale

---

## Reading List

- [ ] [Anthropic — Contextual Retrieval](https://www.anthropic.com/news/contextual-retrieval)
- [ ] [Microsoft — GraphRAG paper and repo](https://github.com/microsoft/graphrag)
- [ ] [RAGAS — RAG evaluation framework](https://docs.ragas.io/)
- [ ] [LangChain RAG tutorials](https://python.langchain.com/docs/tutorials/rag/) (for patterns)
- [ ] ["From Local to Global" — GraphRAG community summaries paper](https://arxiv.org/abs/2404.16130)

---

*Last updated: 2026-04-04*
