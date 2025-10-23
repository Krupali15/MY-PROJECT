# MY-PROJECT

The **Darwin Memory System** is a modular framework designed to store, retrieve, and manage contextual data efficiently.  
It supports ingestion from text and image sources, performs deduplication and caching, and uses hybrid (TF-IDF + vector) indexing for scalable memory retrieval.



## 🧠 Overview

This project implements the internal **Memory Engine** that powers Darwin’s contextual understanding.  
It can process, normalize, and store incoming data, then later retrieve it using keyword and semantic search.  
The main focus is on modularity, scalability, and clean separation between ingestion, storage, and retrieval layers.

---

## ⚙️ Key Features

- 🚀 **FastAPI-based interface** for easy integration  
- 🧩 **Hybrid indexing** using both TF-IDF and cosine similarity  
- 🧠 **Policy-based ranking** and rule-based compaction  
- 🧹 **Deduplication, retention, and caching** for efficiency  
- 💾 **SQLite-backed memory store** for persistence  
- 🧱 **Clean modular structure** easy to extend or debug  

---

## 🗂️ Folder Structure
darwin_memory/

├── admin_api.py # Administrative endpoints for managing memory

├── api.py # Core API routes and service entrypoints

├── cache.py # Caching logic for fast context retrieval

├── compaction.py # Handles cleanup and log compaction

├── dedupe.py # Deduplication of similar entries

├── ingestion_image.py # Image ingestion pipeline

├── ingestion_text.py # Text ingestion and embedding generation

├── main.py # Main script to start the memory service

├── polish.py # Cleans and normalizes data before indexing

├── ratelimit.py # API rate limiter

├── retention.py # Retention logic for memory entries

├── retrieval.py # Context retrieval logic

├── scoring.py # Ranking and scoring module

├── storage.py # Storage and SQLite backend


---

## 🧱 Architecture Overview

![System Design](https://github.com/user-attachments/assets/ae571174-8112-4db3-81f6-cdf348454f89)



The system follows a simple but powerful architecture:

1. **FastAPI Layer**  
   Handles API endpoints like `/ingest_text`, `/ingest_image`, `/retrieve_context`, and `/explain/{request_id}` for external requests.

2. **MemoryService**  
   The core orchestrator combining multiple components to manage indexing, policy control, and ranking.

3. **HybridIndex**  
   Uses two indexing techniques:  
   - **Keyword Index (TF-IDF)** for lexical search  
   - **Vector Index (Cosine Similarity)** for semantic similarity search  

4. **PolicyEngine**  
   Applies business rules, filters, and access control before ranking.

5. **Ranker**  
   Scores and sorts retrieved entries based on policy and similarity.

6. **Packer**  
   Performs **rule-based compaction** — merging redundant entries to save space.

7. **Memory DB (SQLite)**  
   Stores normalized and compacted data. Serves index data back to the retrieval engine.

8. **Normalization & Policy Tagging**  
   Converts raw input into clean, structured memory entries and attaches policy tags.

9. **Ingestors**  
   Handle text or image input streams, calling the normalization and indexing layers.

---

## 🧩 How It Works

1. Input (text or image) is sent via the FastAPI endpoints.  
2. The ingestors normalize data and apply policy tags.  
3. HybridIndex indexes the content both lexically and semantically.  
4. Retrieval requests query the index, and Ranker returns the most relevant results.  
5. Packer and Retention modules keep the memory optimized over time.

---

## 🧪 Setup & Run

### 1. Create Virtual Environment
```bash
python3 -m venv .venv
source .venv/bin/activate




