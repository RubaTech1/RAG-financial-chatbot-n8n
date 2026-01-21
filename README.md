# RAG Financial Chatbot (n8n)

A Retrieval-Augmented Generation (RAG) chatbot built using **n8n**, designed to answer financial questions accurately based **only on official financial reports**.

##  Project Idea
Can we ask financial questions and get **accurate, grounded answers** without hallucination?

This project implements a **RAG-based Financial Chatbot** that analyzes quarterly financial reports (Q1–Q4) and answers user questions **strictly from the provided documents**.

If the requested information does not exist in the data, the chatbot explicitly responds:
> **"No current information is available on this subject."**

##  Data Source
- Official financial reports (used in this project):
  - Apple Investor Relations (Quarterly Reports)
  - https://www.apple.com/newsroom/archive/

Only data from these reports is indexed and used for answering questions.

##  System Architecture

### 1️⃣ Knowledge Base Pipeline (n8n)
- Triggered manually or on schedule
- Searches and retrieves report files
- Cleans and prepares content
- Downloads and processes documents
- Generates embeddings using **OpenAI Embeddings**
- Stores vectors in **Pinecone Vector Database**

### 2️⃣ RAG Chatbot Pipeline
- Receives user queries
- Uses an AI Agent with:
  - Vector Store Retriever (Pinecone)
  - OpenAI Chat Model
  - Simple memory
- Retrieves the most relevant chunks
- Generates answers grounded strictly in retrieved context

##  Key Challenges Addressed
- **Chunking financial data correctly** to retrieve precise numerical values
- Preventing the model from:
  - Mixing numbers across different reports
  - Using correct values in the wrong financial context
- Avoiding hallucination in sensitive financial information

##  Why RAG?
- Financial data is **highly sensitive**
- Accuracy is more important than fluency
- RAG ensures answers are:
  - Verifiable
  - Context-aware
  - Source-grounded

##  Tech Stack
- n8n (workflow automation)
- OpenAI (Chat Models & Embeddings)
- Pinecone (Vector Database)
- Recursive Character Text Splitter
- Retrieval-Augmented Generation (RAG)

##  How It Works
1. Financial reports are ingested and embedded into a vector database
2. User asks a financial question
3. Relevant report sections are retrieved
4. The AI agent generates an answer strictly based on retrieved context

## 🚀 Future Improvements
- Improve chunking strategy for financial tables
- Reduce token consumption
- Add citation references per answer
- Support multi-company financial reports
- Deploy as a web-based chatbot


