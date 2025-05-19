
# Plan:

**1. RAG quickstart & Motivation (5 min)**

- Quick recap: Retriever + Generator
- Why KR matters: ensures retrieval is meaningful and augmentation effective

**2. KR in RAG: Data Preparation & Indexing (15 min)**

- Chunking strategies: how we split documents (paragraph, sentence, fixed size, etc.)
- Metadata enrichment: tags, categories, provenance
- Vector embeddings: main KR for retrieval, model choice, vector DBs

**3. KR in RAG: Retrieval (10-15 min)**

- Query representation: embedding queries, possible expansion/augmentation
- Similarity search: measuring closeness in embedding space
- Hybrid search: dense (vector) + sparse (keyword/BM25)
- Structured KR: brief nod to KGs and how they can add explicit, factual details (without deep dive)

**4. KR in RAG: Generation (5 min)**

- Structuring context for LLMs: formatting retrieved chunks and metadata
- LLM grounding: using retrieved knowledge for factual, attributed answers

**5. Challenges & Future Trends (5-7 min)**

- Challenges: embedding quality, chunking, retrieval fusion, scalability, evaluation
- Future: better embeddings, automated chunking/metadata, advanced query analysis, joint optimization
