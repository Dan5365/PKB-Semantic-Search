```markdown
# Intelligent Personal Knowledge Base — Semantic Search Module

## 📌 Project Overview
* **English:** Development of a Semantic Search Module for a Personal Knowledge Base Based on PostgreSQL/pgvector with an Investigation into Search Strategy Effectiveness
* **Қазақша:** PostgreSQL/pgvector негізіндегі дербес білім базасына арналған семантикалық іздеу модулін әзірлеу және іздеу стратегияларының тиімділігін зерттеу
* **Русский:** Разработка модуля семантического поиска для персональной базы знаний на основе PostgreSQL/pgvector и исследование эффективности стратегий поиска

---

## 👥 Team Members & Responsibilities
* **Adilbekuly Daniyal** (SE-2407) — *Lead Backend & Database Architect*
  * PostgreSQL + `pgvector` schema design, HNSW/IVFFlat vector indexing, hybrid search algorithm implementation.
* **Tapishev Daniyal** (SE-2407) — *Backend & Frontend Engineer*
  * REST API development (Notes Service), React UI implementation, search strategy switcher, E2E & unit testing.
* **Marat Erkanat** (SE-2407) — *Integration, QA & Benchmarking Engineer*
  * Docker infrastructure, CI/CD pipelines, search strategy benchmarking (Precision@K, Recall@K, MRR), YouTrack management.

**Academic Supervisor:** Aitmukhanbetova Elvira Aitmukhanbetkyzy

---

## 🎯 Problem Statement & Core Objectives
Modern personal knowledge bases (PKB) accumulate large volumes of unstructured notes and documents. Traditional keyword-based search (sparse retrieval) struggles with context, synonyms, and semantic meaning. 

This project implements a multi-service architecture centered around a **PostgreSQL/pgvector** database to provide an intelligent hybrid search engine. The project evaluates three distinct retrieval strategies:
1. **Sparse Retrieval:** Full-Text Search (FTS / BM25) in PostgreSQL.
2. **Dense Retrieval:** Vector embeddings and similarity search via `pgvector` (Cosine / L2 distance with HNSW indexes).
3. **Hybrid Retrieval:** Reciprocal Rank Fusion (RRF) combining Sparse and Dense scores.

---

## 🛠 Tech Stack
* **Database & Vector Search:** PostgreSQL 16+, `pgvector` extension
* **Backend Framework:** Python 3.11+, FastAPI, SQLAlchemy 2.0, Pydantic v2
* **ML & Embeddings:** HuggingFace `sentence-transformers` (`all-MiniLM-L6-v2`)
* **Frontend:** React 19, Tailwind CSS, Vite
* **DevOps & Testing:** Docker, Docker Compose, pytest, YouTrack, GitHub Actions

---

## 🏗 Microservice Architecture


```

```
                   ┌─────────────────────────┐
                   │  React 19 Single Page   │
                   │   Frontend (Port 5173)  │
                   └────────────┬────────────┘
                                │
           ┌────────────────────┼────────────────────┐
           │ REST API           │ REST API           │ REST API
           ▼                    ▼                    ▼
 ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐
 │   Auth Service   │  │  Notes Service   │  │ Search & Embedding│
 │   (Port 8000)    │  │   (Port 8001)    │  │  Module (8002)   │
 └────────┬─────────┘  └────────┬─────────┘  └────────┬─────────┘
          │                     │                     │
          │ JWT Verify          │ CRUD / SQL          │ Vector / FTS
          ▼                     ▼                     ▼
 ┌──────────────────────────────────────────────────────────────┐
 │             PostgreSQL 16 + pgvector Extension               │
 │         (User Data, Notes, Vector Embeddings & FTS)          │
 └──────────────────────────────────────────────────────────────┘

```

```

---

## 🔗 Project Management & Useful Links
* **YouTrack Board:** [PKB YouTrack Project Workspace](https://youtrack.jetbrains.com/) *(Замените на вашу прямую ссылку)*
* **API Documentation:**
  * Auth Service API: `http://localhost:8000/docs`
  * Notes Service API: `http://localhost:8001/docs`
  * Search Engine API: `http://localhost:8002/docs`

---

## 📚 Open Access References & Literature Review Sources

All referenced literature sources are freely accessible (Open Access / ArXiv):

1. **pgvector Repository & Docs:** [PostgreSQL Vector Similarity Search Extension](https://github.com/pgvector/pgvector)
2. **Dense Passages Retrieval (DPR):** [Karpukhin et al. (2020) - Dense Passage Retrieval for Open-Domain Question Answering (ArXiv)](https://arxiv.org/abs/2004.04906)
3. **Reciprocal Rank Fusion (RRF):** [Cormack et al. - Reciprocal Rank Fusion outperforms Condorcet and individual Rank Learning Methods (SIGIR Open)](https://plapante.faculty.uconn.edu/posts/2023-11-26-rrf.html)
4. **Sentence-BERT:** [Reimers & Gurevych (2019) - Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks (ArXiv)](https://arxiv.org/abs/1908.10084)
5. **HNSW Indexing:** [Malkov & Yashunin (2018) - Efficient and robust approximate nearest neighbor search using Hierarchical Navigable Small World graphs (IEEE/ArXiv)](https://arxiv.org/abs/1603.09320)
6. **BM25 Search Algorithm:** [Robertson & Zaragoza (2009) - The Probabilistic Relevance Framework: BM25 and Beyond (Open Access PDF)](https://www.ftweb.org/pdf/bm25.pdf)
7. **Vector Databases in Practice:** [Pan et al. (2023) - Survey on Vector Database Management Systems (ArXiv)](https://arxiv.org/abs/2310.11703)
8. **Information Retrieval Evaluation:** [Manning, Raghavan, Schütze - Introduction to Information Retrieval (Free Online Textbook by Stanford)](https://nlp.stanford.edu/IR-book/information-retrieval-book.html)

---

## 🚀 Quick Start & Local Setup

### Prerequisites
* Docker Engine 24.0+ & Docker Compose 2.0+
* Git

### Installation & Run

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/Dan5365/Secure-Notes-API-FastAPI-.git](https://github.com/Dan5365/Secure-Notes-API-FastAPI-.git)
   cd Secure-Notes-API-FastAPI-

```

2. **Start system via Docker Compose:**
```bash
docker-compose up --build -d

```


3. **Verify running services:**
* Frontend: `http://localhost:5173`
* Backend API: `http://localhost:8001/docs`



```

***

### Что сделать прямо сейчас:
1. Замените содержимое вашего файла `README.md` в корнях репозитория на этот текст.
2. Вставьте туда вашу настоящую ссылку на **YouTrack** (когда создадите проект).
3. Сделайте коммит и отправьте изменения на GitHub:
   ```bash
   git add README.md
   git commit -m "PKB-1: Update README.md with project scope, pgvector architecture and literature links"
   git push origin main

```
