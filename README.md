
---

## 📸 Features

- Upload PDF documents
- Automatic chunking
- 384-dimensional embedding generation
- Vector insertion into Endee
- Similarity-based retrieval
- RAG-based contextual answer generation
- Clean UI interface

---

## 🧠 Design Decisions

### 🔹 Why separate text storage from vector DB?

To keep vector index lightweight and optimized for search speed, textual metadata is stored in application memory while Endee stores only vectors.

This mirrors production-grade architecture where vector DB handles embeddings and external store handles document content.

---

### 🔹 Why RAG?

RAG reduces hallucination by grounding LLM responses in retrieved context.

---

## 🚀 Future Improvements

- Persistent metadata storage (Redis / PostgreSQL)
- Streaming LLM responses
- Conversation memory
- Multi-document indexing
- Authentication layer
- Dockerized full-stack deployment

---

## 📊 Example Use Case

Upload a resume PDF → Ask:

"Summarize key technical skills"

The system retrieves relevant chunks and generates a contextual summary.

---

## 📜 License

This project uses Endee (Apache License 2.0).

---

## 👨‍💻 Author

Mayank Maletha  
Machine Learning Enthusiast | Backend Developer
