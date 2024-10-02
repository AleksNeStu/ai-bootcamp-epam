# Task
Think and provide a strategy to chunk and link chunks between each other if you're asked to build a RAG application over emails & project reports of a project group. There are A LOT of documents and since documents are large basic RAG was performing quite poor

Please consider following:

project reports are too large to fit in one chunk
users of a system are asking questions like
give me all project initiatives that are in RED status and overview of their issues?
give me overview of team of project X
What is the strategy to manage context will allow system to answer this questions efficiently?
In the submission define your strategy to work with information (like - we need to use a hierarchical chunking over project documents, use vector clustering to identify the projects and user hybrid rag on top of that - but a bit more verbose, identify key techniques and define it's parameter - so if you're using hierarchical chunking - explain why and approximately with what parameters). Explain approximately how this design should work to help to answer to given questions (and why basic RAG will perform poor on that)

There is no precise answer for this task - but way of thinking and reasoning is the key

# Solution overview
To build an effective RAG (Retrieval-Augmented Generation) application for handling emails and project reports in a large project group, we need a sophisticated approach to chunking, indexing, and retrieval.

Proposed strategy that could work well for this scenario:
[rag-strategy](rag-strategy.md)

Below is comprehensive strategy for building a RAG application to handle emails and project reports effectively. This approach addresses the challenges of dealing with large documents and complex queries in a project management context.
The key components of this strategy include:

- Hierarchical chunking
- Metadata extraction and indexing
- Vector embeddings and clustering
- Hybrid retrieval approach
- Dynamic context window
- Query understanding and decomposition

This design should work well for answering the given types of questions by combining precise metadata filtering with semantic search and hierarchical navigation. It allows for quick identification of relevant projects or teams while also providing the flexibility to dive into detailed information when needed.


