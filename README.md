# 🚀 Vector Database from Scratch in C++

A high-performance **Vector Database** built in C++ implementing **HNSW**, **KD-Tree**, and **Brute Force** search, along with a **Retrieval-Augmented Generation (RAG)** pipeline using a local LLM via Ollama.

> Built and extended by **Kartik Gautam** to understand and optimize large-scale semantic search systems and AI-powered retrieval pipelines.

---

## ⭐ Key Highlights

* Implemented **HNSW (Hierarchical Navigable Small World)** from scratch for efficient approximate nearest neighbor search
* Designed a **modular vector database engine** supporting multiple algorithms and distance metrics
* Built a **RAG pipeline** integrating embeddings + retrieval + LLM generation
* Developed a **REST API server in C++** for real-time querying and benchmarking
* Compared performance of HNSW, KD-Tree, and Brute Force with latency measurements

---

## What This Project Does

| Feature                     | Description                                                                     |
| --------------------------- | ------------------------------------------------------------------------------- |
| **3 Search Algorithms**     | HNSW (production-grade), KD-Tree, Brute Force — run all three and compare speed |
| **3 Distance Metrics**      | Cosine similarity, Euclidean distance, Manhattan distance                       |
| **16D Demo Vectors**        | 20 pre-loaded semantic vectors across 4 categories (CS, Math, Food, Sports)     |
| **2D PCA Scatter Plot**     | Live visualization of semantic space — watch clusters form                      |
| **Real Document Embedding** | Paste any text → Ollama embeds it with `nomic-embed-text` (768D)                |
| **RAG Pipeline**            | Ask questions about your documents → HNSW retrieves context → local LLM answers |
| **Full REST API**           | CRUD endpoints: insert, delete, search, benchmark, hnsw-info                    |

---

## 🧠 What I Learned

* Trade-offs between exact and approximate nearest neighbor search
* Why KD-Tree fails in high-dimensional spaces (curse of dimensionality)
* How HNSW achieves near O(log N) performance using graph-based search
* Designing scalable backend systems in C++
* Integrating AI systems (LLMs + embeddings) into traditional systems

---

## How It Works

```
Your Text
    │
    ▼
Ollama (nomic-embed-text)          ← converts text to a 768-dimensional vector
    │
    ▼
HNSW Index (C++)                   ← indexes the vector in a multilayer graph
    │
    ▼
Semantic Search                    ← finds nearest neighbors in vector space
    │
    ▼
Ollama (llama3.2)                  ← reads retrieved chunks, generates an answer
    │
    ▼
Answer
```

---

## ⚙️ Prerequisites

You need:

* **C++ Compiler (MSYS2 / g++)**
* **Git**
* **Ollama (Local LLM runtime)**

---

## 🛠️ Setup (Windows)

### 1. Install Dependencies

```powershell
ollama pull nomic-embed-text:latest
ollama pull llama3.2:1b   # recommended for low RAM systems
```

---

### 2. Clone Repository

```powershell
git clone https://github.com/Kartikgtm7/vector-db-cpp-rag.git
cd vector-db-cpp-rag
```

---

### 3. Compile

```powershell
g++ -std=c++17 main.cpp -o db.exe -lws2_32
```

---

### 4. Run

**Terminal 1:**

```powershell
ollama serve
```

**Terminal 2:**

```powershell
.\db.exe
```

---

### 5. Open UI

```
http://localhost:8080
```

---

## 🧪 Features Demo

### 🔍 Search

* Query semantic vectors using HNSW / KD-Tree / Brute Force
* Compare latency across algorithms

### 📄 Document Embedding

* Paste text → auto chunking → embedding → storage

### 🤖 RAG (Ask AI)

* Query documents
* Retrieve relevant chunks
* Generate answers using local LLM

---

## ⚡ Performance Notes

* HNSW significantly outperforms brute force for larger datasets
* KD-Tree performs well for low-dimensional data but degrades in high dimensions
* LLM inference latency depends on model size (`llama3.2:1b` recommended)

---

## 🧱 Project Structure

```
VectorDB/
├── main.cpp        ← C++ backend (HNSW, KD-Tree, BruteForce, REST API, RAG)
├── httplib.h       ← HTTP server library
├── index.html      ← Frontend UI
└── README.md
```

---

## 🚧 Future Improvements

* Multi-threaded query execution
* Disk persistence for large-scale datasets
* Benchmarking on 100K+ vectors
* Hybrid search (keyword + vector)
* Query caching for performance optimization

---

## 📌 Key Concepts Used

* Approximate Nearest Neighbor (ANN)
* Graph-based search (HNSW)
* High-dimensional vector similarity
* Retrieval-Augmented Generation (RAG)
* REST API design in C++

---

## 📄 License

MIT License — free to use and modify.
