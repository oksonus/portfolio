🔹 Project Overview

This project demonstrates how PostgreSQL can be transformed into a vector database using the pgvector extension.

Instead of relying on traditional keyword-based search, text is converted into embeddings — numerical vectors that capture the meaning of the text. These embeddings are stored in PostgreSQL and used to enable semantic search, where results are ranked based on meaning rather than exact word matches.

To keep the example simple, the dataset uses short movie descriptions. However, the same approach is widely used in real-world systems involving:

Documents
Articles
Reports
Large knowledge bases
🔹 How it works

The system follows a simple but powerful pipeline:

Text → Embeddings using a Sentence Transformer model
Embeddings → Stored in PostgreSQL via pgvector
Query → Converted into an embedding
Vectors → Compared using cosine similarity
Results → Ranked and returned
🔹 Cosine similarity (search mechanism)

Cosine similarity is the core of the search process and is executed inside PostgreSQL, not Python.

Python (SentenceTransformer) → generates embeddings
PostgreSQL (pgvector) → performs similarity calculation

The comparison uses:

embedding <=> query_vector
<=> is provided by the pgvector extension
It calculates cosine distance (lower value = more similar)

To make results easier to interpret, the distance is converted into a similarity score:

1 - (embedding <=> query_vector)
1.0 → very similar meaning
0.0 → low similarity
🔹 PostgreSQL and semantic search

With pgvector enabled, PostgreSQL is capable of performing semantic search over embeddings by directly comparing vectors.

However:

PostgreSQL does not generate embeddings
An external model (e.g. Python + SentenceTransformer) is used for that step

Once embeddings are generated, PostgreSQL handles:

Storage
Similarity computation
Ranking of results

If embeddings already exist, PostgreSQL alone is sufficient to perform semantic search.

🔹 Key idea

This system enables semantic search instead of keyword search, allowing results to be retrieved based on:

Meaning
Context
Conceptual similarity

rather than exact text matching.
