🔹 Project Overview

This project shows how PostgreSQL can be used as a vector database by enabling the pgvector extension.

Instead of searching text using keywords, text is converted into embeddings (vectors that represent meaning). These vectors are stored in PostgreSQL and used for semantic search, where results are based on meaning rather than exact words.

The example uses short movie descriptions to keep things simple, but most real-world use cases involve larger text such as documents, reports, or articles. The same approach can be applied by embedding and storing larger text.

🔹 How it works
Text → converted into embeddings using a Sentence Transformer model
Embeddings → stored in PostgreSQL using pgvector
Query → converted into an embedding
Vectors → compared using cosine similarity
Results → ranked and returned
🔹 Cosine similarity (where it is used)

Cosine similarity is used during the search step inside PostgreSQL, not in Python.

Python (SentenceTransformer) → generates embeddings
PostgreSQL (pgvector) → calculates similarity

The comparison is done using:

embedding <=> query_vector
<=> is provided by the pgvector extension
It calculates cosine distance (smaller = more similar)

To make it easier to read, it is converted into a score:

1 - (embedding <=> query_vector)
Closer to 1 → more similar
Closer to 0 → less similar
🔹 PostgreSQL and semantic search

PostgreSQL (with pgvector) can perform semantic search by comparing vector embeddings.

However, it does not generate embeddings from text on its own.

An external model (e.g. Python + SentenceTransformer) is used to create embeddings
PostgreSQL stores and compares those embeddings

If embeddings are already available, PostgreSQL alone is enough to perform semantic search.

🔹 Key idea

This system performs semantic search, meaning it finds results based on meaning and context, not exact keyword matches.

