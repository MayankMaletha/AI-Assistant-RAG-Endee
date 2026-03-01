# 🚀 AI Assistant using RAG + Endee Vector Database

An AI-powered Assistant built using Endee Vector Database and Retrieval-Augmented Generation (RAG).

This system allows users to upload PDF documents and ask contextual questions. It retrieves relevant document chunks using vector similarity search and generates accurate responses using an LLM.

---

## 📌 Problem Statement

Traditional keyword-based search fails to capture semantic meaning and contextual relevance in long documents.

This project solves that problem by implementing:

- Semantic Search
- Vector Embeddings
- Retrieval-Augmented Generation (RAG)
- High-performance vector similarity search using Endee

---

## 🏗 System Architecture

User → FastAPI Backend → Embedding Model → Endee Vector DB → Groq LLM → Response

### Workflow

1. User uploads a PDF
2. PDF text is extracted and chunked
3. Each chunk is converted into embeddings
4. Embeddings are stored in Endee
5. User asks a question
6. Question is embedded
7. Endee performs similarity search
8. Top-k relevant chunks retrieved
9. Context sent to LLM
10. LLM generates final answer

---

## 🛠 Tech Stack

- **Backend:** FastAPI
- **Vector Database:** Endee (Docker-based)
- **Embedding Model:** sentence-transformers (all-MiniLM-L6-v2)
- **LLM Inference:** Groq (LLaMA 3.1)
- **PDF Processing:** PyPDF2
- **Encoding Format:** MsgPack (Endee search response)

---

## ⚡ Why Endee?

Endee is a high-performance open-source vector database optimized with SIMD acceleration (AVX2/AVX512).

In this project, Endee is used to:

- Store 384-dimensional embeddings
- Perform efficient nearest-neighbor search
- Return vector IDs for contextual retrieval

Search results are decoded from MsgPack format to extract vector similarity scores and IDs.

---

## 📂 Project Structure
endee-/
│
├── app/
│ ├── main.py
│ ├── embedding.py
│ ├── vector_store.py
│ ├── rag_pipeline.py
│ └── storage.py
│
├── frontend/
│ └── index.html
│
├── requirements.txt
├── .env
└── README.md


---

## 🔧 Setup Instructions

### 1️⃣ Clone Repository
git clone <https://github.com/endee-io/endee>
cd endee-


---

### 2️⃣ Start Endee using Docker
docker compose up -d
Ensure Endee runs on: http://localhost:8080


---

### 3️⃣ Create Virtual Environment


python -m venv venv
venv\Scripts\activate

---

### 4️⃣ Install Dependencies


pip install -r requirements.txt


---

### 5️⃣ Add Environment Variables

Create `.env` file:


ENDEE_BASE_URL=http://localhost:8080

INDEX_NAME=research_index
GROQ_API_KEY=your_groq_api_key

---

### 6️⃣ Run Backend


uvicorn app.main:app --reload


Backend runs on:


http://127.0.0.1:8000


---

### 7️⃣ Open Frontend

Open:


frontend/index.html
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
