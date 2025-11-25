# Data Tier Manifest

This directory represents the data storage layer of the RAG application.

1.  **Firestore (In Use):** The current application uses Firebase Firestore for secure, user-specific document content storage, located at:
    `/artifacts/{appId}/users/{userId}/documents`

2.  **Vector Database (Conceptual):** In a scalable RAG system, document chunks would be converted into vector embeddings and stored here (e.g., Pinecone, ChromaDB, Weaviate) to enable fast semantic retrieval.

3.  **File Storage (Conceptual):** Binary files (PDFs, DOCX) would be stored in Firebase Storage or AWS S3, and only the extracted text content would be kept in Firestore/Vector DB.
