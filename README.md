# Spotify RAG Proof of Concept 🎶

This repository showcases a Retrieval Augmented Generation (RAG) system for music recommendation. It demonstrates how to leverage Knowledge Graphs (KGs) and Vector Embeddings to provide nuanced and accurate answers to music-related queries, addressing the limitations of LLMs regarding specific domain data.

## 🧠 Knowledge Representation in RAG

Choosing the right data structure is crucial for efficient RAG retrieval:

Vectorized Embeddings: Convert text into numerical vectors for semantic similarity search; good for finding similar concepts but can miss nuanced relationships.

Knowledge Graphs (KGs): Represent information as interconnected nodes and relationships, enabling precise, context-rich retrieval for complex queries.

Hybrid GraphRAG: Combines vector embeddings for semantic search and knowledge graphs for structured context, offering versatile and accurate query handling.

## 🧑‍💻 Demo: Spotify Knowledge Graph & RAG Implementation

This demo transforms a tabular Spotify dataset into a connected Knowledge Graph in Neo4j, serving as the "Knowledge Base" for a RAG system to answer music-related queries.

**Expected Flow**: User asks question about songs -> question is vectorized -> relevant data retrieved from Neo4j -> LLM generates response with knowledge base data.

### Initialization & Data Preparation

- **Libraries**: `neo4j`, `neo4j_graphrag`, `sentence_transformers`, `google-generativeai`, `pandas`.
- **API Keys**: Configured for Neo4j and Google Generative AI.
- **Models**: `SentenceTransformerEmbeddings(model="all-MiniLM-L6-v2")` for embeddings, `GeminiLLM(model_name="gemini-1.5-flash-001")` as the generative LLM.
- **Data**: A Spotify dataset (~900k songs, sampled to 20k) is loaded into a Pandas DataFrame. It includes `Artist(s)`, `song`, `text` (lyrics), `emotion`, `Length`, `Album`, `Genre`, `Energy`, `Popularity`, `Danceability`, `Positiveness`.

### Neo4j Ingestion: Building the Graph

Music is inherently connected, making it ideal for a Knowledge Graph. The following relationships are established in Neo4j to enable powerful contextual queries:

- `Artist`-[:PERFORMED]->`Song`
- `Song`-[:APPEARS_ON]->`Album`
- `Song`-[:HAS_GENRE]->`Genre`
- `Song`-[:EVOKES]->`Emotion`
- `Artist`-[:COLLABORATE_WITH]->`Artist` (implicitly via songs)

A vector index named "songIndex" is created on the `Song` node's `embedding` property with an `EMBEDDING_DIMENSION` of 384.
