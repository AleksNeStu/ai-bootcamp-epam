# RAG Strategy for Project Management Documents

## 1. Hierarchical Chunking

We'll use hierarchical chunking to break down large documents while preserving context:

- **Top level**: Entire document summary (300-500 tokens)
- **Mid level**: Section summaries (500-1000 tokens each)
- **Bottom level**: Detailed chunks (1000-1500 tokens each)

Rationale: This allows us to capture both high-level context and detailed information, addressing the issue of project reports being too large for a single chunk.

## 2. Metadata Extraction and Indexing

- Extract key metadata from each document:
  - Project name
  - Team members
  - Project status (RED, AMBER, GREEN)
  - Key dates
  - Main topics/initiatives

- Create a structured index of this metadata, linked to the hierarchical chunks.

Rationale: This enables quick filtering and retrieval based on specific attributes without relying solely on semantic search.

## 3. Vector Embeddings and Clustering

- Generate embeddings for each chunk at all levels of the hierarchy.
- Perform clustering on these embeddings to group related information across documents.
- Use techniques like HDBSCAN or K-means for clustering, with the number of clusters roughly corresponding to the number of major projects or initiatives.

Rationale: This allows for efficient similarity search and helps in identifying overarching themes or related information across different documents.

## 4. Hybrid Retrieval Approach

Combine multiple retrieval methods:

1. **Metadata-based filtering**: Use the structured index for initial filtering.
2. **Vector similarity search**: Find semantically similar chunks across the filtered set.
3. **Hierarchical navigation**: Start with top-level chunks and drill down as needed.

Rationale: This multi-pronged approach allows for both precise (metadata-based) and fuzzy (semantic) matching, improving retrieval accuracy.

## 5. Dynamic Context Window

- Implement a dynamic context window that can expand or contract based on the query complexity and the hierarchical level of retrieved chunks.
- For broad queries, focus on top and mid-level chunks.
- For specific queries, include more detailed bottom-level chunks.

Rationale: This ensures that the most relevant context is provided to the language model without overwhelming it with unnecessary details.

## 6. Query Understanding and Decomposition

- Implement a query understanding module to classify and decompose complex queries.
- For multi-part questions, break them down into sub-queries that can be answered independently and then synthesized.

Rationale: This helps in handling complex queries that might require information from multiple sources or levels of the hierarchy.

## Answering Sample Questions

1. "Give me all project initiatives that are in RED status and overview of their issues?"
   - Use metadata filtering to quickly identify RED status projects.
   - Retrieve top-level summaries of these projects.
   - For each project, fetch mid-level chunks related to issues or challenges.
   - Synthesize this information into a concise overview.

2. "Give me overview of team of project X"
   - Use metadata lookup to identify project X.
   - Retrieve the top-level summary and team-related mid-level chunks.
   - Use vector search to find any additional relevant information about team members across other documents.
   - Compile this information into a coherent team overview.

## Why Basic RAG Would Perform Poorly

A basic RAG approach would struggle with this scenario for several reasons:

1. **Context fragmentation**: Simple chunking would break the continuity of large project reports, losing important context.
2. **Inefficient retrieval**: Without metadata indexing, every query would require a full semantic search, which is slow and less precise for attribute-based queries.
3. **Lack of hierarchical understanding**: Basic RAG can't differentiate between high-level overviews and detailed information, potentially returning irrelevant or overly specific results.
4. **Query complexity**: Simple retrieval methods might not handle multi-part queries effectively, missing important aspects of the question.
5. **Scale issues**: With a large number of documents, basic similarity search might become computationally expensive and less accurate.

This advanced strategy addresses these limitations by providing a more structured, context-aware, and efficient approach to information retrieval and synthesis.

