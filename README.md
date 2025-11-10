# 🤖 RAG Chatbot Pipeline with n8n, OpenAI, and Pinecone

This project demonstrates a **Retrieval-Augmented Generation (RAG)** chatbot workflow built entirely in **[n8n](https://n8n.io/)** — a low-code automation platform.  
The pipeline automates the ingestion of documents from Google Drive, generates embeddings using OpenAI, stores them in Pinecone for vector search, and powers a conversational AI agent that retrieves relevant context before responding.

---

## 🧩 Workflow Overview

The workflow consists of two main stages:

### **1. Document Ingestion**
Triggered automatically when a new file is added to Google Drive.

**Flow:**
1. **Google Drive Trigger** – Detects new file uploads.
2. **Download File** – Fetches the file content.
3. **Recursive Character Text Splitter** – Splits large text into manageable chunks.
4. **OpenAI Embeddings** – Converts text chunks into 1536-dimensional vectors using `text-embedding-3-small`.
5. **Pinecone Vector Store** – Stores the embeddings in a Pinecone index for efficient semantic search.

---

### **2. Conversational Retrieval**
Handles real-time chat queries and context retrieval.

**Flow:**
1. **When Chat Message Received** – Captures user queries.
2. **AI Agent (OpenAI Chat Model)** – Acts as the core reasoning engine.
3. **Pinecone Vector Search** – Retrieves the most relevant document chunks.
4. **OpenAI Chat Model** – Combines the retrieved context and user query to produce an informed response.

---

## 🧠 Architecture

| Component | Description |
|------------|-------------|
| **n8n Cloud** | Orchestrates the RAG pipeline with visual workflow logic |
| **Google Drive** | Source for uploading and monitoring documents |
| **OpenAI API** | Generates embeddings and conversational responses |
| **Pinecone** | Vector database for semantic search (dimension: 1536) |

---

## ⚙️ Setup Instructions

1. **Clone this repo**
   ```bash
   git clone https://github.com/yourusername/rag-chatbot-n8n.git
   cd rag-chatbot-n8n
