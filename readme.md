# MIRA: Memory-Integrated Retrieval Agent

## 🚀 Overview
**MIRA (Memory-Integrated Retrieval Agent)** is a modular, multi-agent system designed to process, retrieve, and query documents at scale. It combines **vectorized memory (Qdrant)**, **state-of-the-art NLP models**, and an intelligent **agent orchestration layer** to deliver highly accurate and context-aware responses.

MIRA is built for systems that demand **precision, scalability, and adaptability** in document intelligence.

---

## ❓ Why MIRA?

- 🧠 **Integrated Memory**  
  Persistent, context-aware memory enables efficient and intelligent document retrieval.

- 🤖 **Multi-Agent Architecture**  
  Each document is handled by a dedicated agent, ensuring granular and scalable processing.

- ⚡ **High Performance Retrieval**  
  Vector similarity search minimizes latency even across large datasets.

- 🔌 **Modular & Extensible**  
  Easily swap embedding models, vector stores, or LLMs.

- 🎯 **Context-Aware Precision**  
  Combines retrieval, planning, and reranking for high-quality responses.

---

## 🌟 Key Features

- **Vectorized Document Storage**  
  Uses HuggingFace embeddings stored in Qdrant for fast similarity search.

- **Dynamic Agent Selection**  
  Query Planner selects the most relevant agents based on context and performance.

- **Custom Reranking**  
  Enhances retrieval accuracy using contextual and statistical scoring.

- **Scalable Pipeline**  
  Designed to handle large-scale document collections efficiently.

- **End-to-End NLP Pipeline**  
  Integrates LLMs like GPT for advanced reasoning and response generation.

---

## 📜 Table of Contents

- [Architecture](#-architecture)
- [Getting Started](#-getting-started)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [Example Workflow](#-example-workflow)
- [File Structure](#-file-structure)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🏗 Architecture

MIRA follows a **modular, multi-agent architecture**:

### 1. Master Agent
Central orchestrator that:
- Routes queries to relevant agents  
- Aggregates responses  
- Works with Query Planner & Reranker  

---

### 2. Document Agent
Handles individual documents:
- Converts documents into embeddings  
- Evaluates query relevance  
- Interfaces with Qdrant  

---

### 3. Query Planner
- Selects relevant agents dynamically  
- Uses query context + historical performance  

---

### 4. Reranker
- Reorders retrieved results  
- Improves accuracy beyond raw similarity scores  

---

### 5. Vector Store
- Powered by Qdrant  
- Stores and retrieves embeddings efficiently  

---

## 🔄 High-Level Workflow

1. Documents are ingested and embedded  
2. Stored in Qdrant vector database  
3. Query is processed by Master Agent  
4. Query Planner selects relevant Document Agents  
5. Results are retrieved and reranked  
6. Final response is generated using LLM  

---

## 🛠 Getting Started

### 1. Prerequisites

- Python 3.9+  
- Docker  
- Qdrant instance (local or cloud)  
- OpenAI API Key  

---

### 2. Installation

#### Clone Repository
```bash
git clone https://github.com/your-org/mira.git
cd mira

```

### Install Dependencies
```bash
pip install -r requirements.txt

```

### Environment Setup
Create a .env file in the root directory

```bash
OPENAI_API_KEY=your-openai-key
QDRANT_HOST=localhost
QDRANT_PORT=6333
COLLECTION_NAME=mira_documents
VECTOR_SIZE=384
VECTOR_DISTANCE=COSINE

```

### Start Qdrant
Run Qdrant locally using Docker:

```bash
docker run -p 6333:6333 -p 6334:6334 \
    -v $(pwd)/qdrant_storage:/qdrant/storage:z \
    qdrant/qdrant

```

### Configuration
| Setting         | Value                                  |
| --------------- | -------------------------------------- |
| Embedding Model | sentence-transformers/all-MiniLM-L6-v2 |
| Language Model  | gpt-4                                  |
| Vector Size     | 384                                    |
| Distance Metric | COSINE                                 |


### Usage
```bash
bash comman.sh

```

### Run Custom Query
```bash
python main.py --query "What is neural attention?" --docs_path "docs/sample.pdf"

```

### Logs
```bash
tail -f logs/app.log

```

### 📂 File Structure
```bash
.
├── agents/
│   ├── document_agents.py
│   └── master_agent.py
├── modules/
│   ├── query_planner.py
│   └── reranker.py
├── index/
│   └── vector_store.py
├── utils/
│   ├── logger.py
├── config/
│   └── config.py
├── docs/
├── logs/
├── Dockerfile
├── comman.sh
└── README.md

```

### Contributing
Contributions are welcome!

1. Fork the repository
2. Create a new branch (feature/your-feature)
3. Commit your changes
4. Push to your branch
5. Open a Pull Request

- For major changes, please open an issue first to discuss your ideas.

### License
This project is licensed under the MIT License.

### ✨ Closing Note

MIRA isn’t just a document retrieval system—it's a step toward building intelligent, memory-aware AI systems capable of reasoning over large-scale knowledge bases with precision and efficiency.