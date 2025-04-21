# 🤖 DocuBot AWS

**DocuBot AWS** is a technical support chatbot designed to guide new users through basic AWS concepts (e.g., IAM, EC2, S3). Built as a demo, it leverages modular, cost-efficient technologies to deliver an interactive and scalable user experience. This project implements Retrieval-Augmented Generation (RAG) for enhanced knowledge base interaction.

---

## 📋 Table of Contents

1. [Overview](#overview)
2. [Key Features](#key-features)
3. [Architecture](#architecture)
4. [Technology Stack](#technology-stack)
5. [Specifications](#specifications)
6. [Local Implementation Plan](#local-implementation-plan)
7. [Deployment](#deployment)
8. [Optimization Recommendations](#optimization-recommendations)
9. [Contribution](#contribution)
10. [License](#license)

---

## 🌟 Overview

**Objective**: Help new AWS users understand foundational concepts (IAM, EC2, S3) through an accessible and interactive chatbot.

**Core Technologies**:
- **Frontend**: React.js with options for Twilio + WhatsApp API.
- **RAG**: Retrieval-Augmented Generation using LangChain and OpenAI.
- **Storage**: FAISS/ChromaDB embeddings for efficient knowledge retrieval.
- **Infrastructure**: Serverless (AWS Lambda, API Gateway) with Terraform IaC.

---

## ✨ Key Features

1. **Interactive Chat Interface**:
   - Built with React.js for a seamless user experience.
   - Includes support for WhatsApp API through Twilio (optional).

2. **Knowledge Base Integration**:
   - Retrieval-Augmented Generation (RAG) for intelligent responses.
   - Knowledge stored as embeddings with FAISS/ChromaDB.

3. **Cost-Efficient Hosting**:
   - Serverless backend using AWS Lambda.
   - Free-tier friendly for MVP deployment.

4. **Error Handling**:
   - Graceful fallback to FAQs for ambiguous queries.
   - Retry mechanisms for API rate-limiting.

5. **Scalability**:
   - Modular design supports enhancements like voice processing (AWS Transcribe) and advanced role-based functionality.

---

## 🏗️ Architecture

```
[User]
   │
   ▼
[React Frontend]
   │
   ▼
[API Gateway (REST)]
   │
   ▼
[AWS Lambda (Router)]
   ├──▶ [LangChain RAG] → [FAISS/ChromaDB] → [S3 FAQs]
   ├──▶ [Twilio Webhook] (Optional: Fallback for WhatsApp)
   └──▶ [Redis Cache (for frequent responses)]

Error Flows:
1. Ambiguous Query → Contextual clarification.
2. API Limit → Retry queue with exponential backoff.
3. Invalid Term → Phonetic search fallback (e.g., Soundex).
```

---

## 💻 Technology Stack

### **Frontend**
- **React.js**: Interactive UI for user queries.
- **Axios**: For HTTP requests to the backend.
- **LocalStorage**: Caching recent user queries.

### **Backend**
- **LangChain**: RAG for intelligent query handling.
- **FAISS/ChromaDB**: Vector database for embedding storage.
- **Flask/FastAPI**: Lightweight API for routing and processing.
- **Redis** (Optional): Caching frequent responses.

### **Infrastructure**
- **Serverless**: AWS Lambda + API Gateway for scalable backend processing.
- **Terraform**: Infrastructure as Code (IaC) for resource provisioning.
- **CI/CD**: GitHub Actions for automated deployments.

---

## 🛠️ Specifications

| **Module**     | **Functionality**                  | **Technology**       | **Complexity** (1-5) | **Dependencies**         |
|-----------------|-----------------------------------|-----------------------|-----------------------|--------------------------|
| **Frontend**    | User input/output and chat widget | React.js             | 2                     | Axios                    |
| **RAG**         | Semantic search and response gen  | LangChain            | 4                     | OpenAI API, FAISS        |
| **Storage**     | Embedding storage for FAQs        | FAISS/ChromaDB       | 3                     | SentenceTransformers     |
| **Backend API** | Routing and request handling      | Flask/FastAPI        | 3                     | LangChain, Redis (opt.)  |
| **Cache**       | Frequent query storage            | Redis/SQLite         | 2                     | Redis (opt.), Local DB   |
| **Monitoring**  | Metrics and error logging         | Prometheus + Grafana | 3                     | Grafana, Prometheus      |

---

## 🧑‍💻 Local Implementation Plan

### **Minimum Requirements**
- **Hardware**: 8GB RAM, 4-core CPU, 20GB SSD.
- **Software**:
  - Python 3.10+
  - Node.js 18+

### **Step-by-Step Guide**

1. **Set Up Virtual Environment**:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

2. **Install Dependencies**:
   ```bash
   pip install langchain faiss-cpu chromadb flask
   npm install react axios
   ```

3. **Configure Embeddings**:
   ```python
   from langchain.vectorstores import FAISS
   db = FAISS.from_texts(["IAM: Manage users...", "S3: Store objects..."], embeddings)
   ```

4. **Run Backend**:
   ```bash
   flask run --host=0.0.0.0 --port=5000
   ```

5. **Run Frontend**:
   ```bash
   npm run start
   ```

6. **Test API Locally**:
   ```bash
   curl -X POST http://localhost:5000/ask -H "Content-Type: application/json" -d '{"question": "What is EC2?"}'
   ```

---

## 🚀 Deployment

### **Backend Deployment**
- **Option 1**: AWS Lambda + API Gateway (via Terraform)
- **Option 2**: Docker container on ECS Fargate.

### **Frontend Deployment**
- **Option 1**: Netlify (React app).
- **Option 2**: GitHub Pages.

---

## 💰 Optimization Recommendations

1. **Cost-Efficient NLP**:
   - Use **SentenceTransformers** for local embeddings instead of OpenAI.
   - Leverage **Rasa OSS** for self-hosted intent detection.

2. **Free-Tier Friendly**:
   - **AWS Free Tier**: 1M API Gateway calls/month, 1M Lambda invocations/month.
   - **OpenAI Free Credits**: $18 for first month.
   - **Twilio**: $15 trial credits for WhatsApp integration.

3. **Caching Strategy**:
   - **Hot Data**: Redis for top 50 frequent queries.
   - **Cold Data**: FAISS/ChromaDB for all embeddings.

4. **Scalability**:
   - Add Prometheus + Grafana for monitoring response times and query accuracy.
   - Use AWS Transcribe for voice-based queries (future enhancement).

---

## 🤝 Contribution

Contributions are welcome! Follow these steps:
1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature/new-feature
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add new feature"
   ```
4. Push the branch:
   ```bash
   git push origin feature/new-feature
   ```
5. Open a Pull Request.

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.
