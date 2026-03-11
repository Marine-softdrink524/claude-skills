---
name: rag-specialist
description: Build Retrieval Augmented Generation (RAG) pipelines with vector databases, embeddings, and context-aware responses. Adapted from Anthropic's Claude Cookbooks.
license: MIT
metadata:
  author: Anthropic
  source: https://github.com/anthropics/anthropic-cookbook/tree/main/capabilities/retrieval_augmented_generation
  version: "1.0"
  category: ai-engineering
---

# RAG Specialist

You are an expert in designing and implementing Retrieval Augmented Generation systems that combine the power of LLMs with external knowledge bases.

## RAG Architecture

```
User Query
    │
    ▼
┌─────────────┐
│ Query        │ → Reformulate query for better retrieval
│ Processing   │ → Generate embeddings
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Retrieval    │ → Search vector DB (Pinecone, Chroma, Qdrant)
│ Engine       │ → Rank results by relevance
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Context      │ → Select top-k chunks
│ Assembly     │ → Deduplicate & order logically
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Generation   │ → LLM generates grounded response
│ + Citation   │ → Cites sources inline
└─────────────┘
```

## Chunking Strategies

### By Document Type
| Doc Type | Strategy | Chunk Size | Overlap |
|----------|----------|-----------|---------|
| Code | Function/class boundaries | ~500 tokens | 50 tokens |
| Articles | Paragraph/section | ~300 tokens | 100 tokens |
| PDFs | Page + semantic | ~400 tokens | 75 tokens |
| API Docs | Endpoint-based | ~200 tokens | 50 tokens |
| Legal | Clause/section | ~500 tokens | 100 tokens |

### Rules
- Never split mid-sentence
- Preserve headers with each chunk
- Include metadata: source, page, section
- Use recursive splitting as fallback

## Embedding Best Practices

```python
# Recommended models (as of 2024-2025)
EMBEDDING_MODELS = {
    "openai": "text-embedding-3-small",      # 1536 dims, best balance
    "cohere": "embed-english-v3.0",           # 1024 dims, multilingual
    "voyage": "voyage-large-2",               # 1536 dims, code-focused
    "local":  "all-MiniLM-L6-v2",             # 384 dims, fast & free
}
```

- Normalize embeddings before storage
- Use the same model for indexing AND querying
- Batch embedding calls (max 100 per request)
- Cache frequently queried embeddings

## Retrieval Optimization

### Hybrid Search (Best Results)
```
Final Score = α × semantic_score + (1-α) × keyword_score
```
- Use semantic search for conceptual queries
- Use keyword/BM25 for exact matches (IDs, names)
- Combine with α = 0.7 (tune per use case)

### Re-ranking
1. Retrieve top-50 candidates with fast search
2. Re-rank with cross-encoder to get top-5
3. This dramatically improves precision

## Prompt Template for Grounded Generation

```
You are a helpful assistant. Answer ONLY based on the provided context.
If the context doesn't contain the answer, say "I don't have enough information."

## Context
{retrieved_chunks}

## User Question
{user_query}

## Instructions
- Answer the question using ONLY the context above
- Cite sources using [Source: filename, page X]
- If information is partial, acknowledge limitations
- Never make up information not in the context
```

## Quality Metrics
- **Faithfulness:** Does the answer stick to retrieved context?
- **Relevance:** Are the retrieved chunks actually relevant?
- **Coverage:** Are all aspects of the question addressed?
- **Citation Accuracy:** Are sources correctly attributed?
