# Progress Tracker

## Overall Status

| Phase | Status | Started | Notes |
|-------|--------|---------|-------|
| 1. Foundations | 🔜 Not started | — | Parsing, chunking, embeddings |
| 2. Retrieval Layer | ⏳ Waiting | — | Vector stores, hybrid search, eval |
| 3. LLM Layer | ⏳ Waiting | — | Prompting, citation, agentic RAG |
| 4. Knowledge Graphs | ⏳ Waiting | — | Entities, GraphRAG, multi-hop |
| 5. Production | ⏳ Waiting | — | Incremental ingestion, privacy, UI |

---

## Phase 1 — Foundations

### Concepts
- [ ] Understand full RAG pipeline end-to-end
- [ ] Vector similarity search (cosine, ANN)
- [ ] Keyword vs semantic search
- [ ] Why hybrid search wins

### Parsing & Ingestion
- [ ] Explore parsing libraries (unstructured, docling, pymupdf4llm, markitdown)
- [ ] Parse real files, inspect output quality

### Chunking
- [ ] Naive fixed-size chunking with overlap
- [ ] Semantic chunking
- [ ] Structural chunking
- [ ] Read Anthropic's "Contextual Retrieval" post
- [ ] Experiment with chunk sizes

### Embeddings
- [ ] What embedding models do
- [ ] Compare open-source models
- [ ] Compare API models
- [ ] Dimensionality trade-offs
- [ ] HyDE (Hypothetical Document Embeddings)

---

## Phase 2 — Retrieval Layer
*(detailed checkboxes in rag-learning-plan.md)*
- [ ] Vector store setup
- [ ] Hybrid search
- [ ] Reranking
- [ ] Multi-query retrieval
- [ ] Evaluation with RAGAS

---

## Phase 3 — LLM Layer
- [ ] Prompt design for RAG
- [ ] Source citation
- [ ] Context window management
- [ ] Agentic RAG loop

---

## Phase 4 — Knowledge Graphs
- [ ] Knowledge graph concepts
- [ ] Read GraphRAG paper
- [ ] Entity extraction
- [ ] Community summaries
- [ ] Graph + vector hybrid retrieval

---

## Phase 5 — Production
- [ ] Incremental indexing
- [ ] Scale and performance
- [ ] Privacy / encryption
- [ ] Interface (CLI / API / chat)

---

## Log

| Date | What happened |
|------|---------------|
| 2026-04-04 | Project scaffolded. Learning plan created. Repo initialised. |

---

*See `rag-learning-plan.md` for the full detailed checklist.*
