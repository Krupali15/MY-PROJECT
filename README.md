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
│
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
└── util.py # Utility helpers and configs


