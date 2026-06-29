# 🎓 DIEM Virtual Assistant - Advanced NLP & LLM Chatbot

An intelligent conversational agent built to assist students and users with information regarding the **DIEM Department** (Dipartimento di Ingegneria dell'Informazione ed Elettrica e Matematica Applicata) at the University of Salerno. 

This project was developed as part of my Master's Degree in Computer Engineering for Artificial Intelligence. It demonstrates the practical application of **Large Language Models (LLMs)**, **Retrieval-Augmented Generation (RAG)**, and **Agentic Workflows**.

## 🚀 Features

*   **Agentic Workflow (Plan-and-Execute):** Built with LangGraph, the chatbot analyzes the user's intent, breaks down complex queries into manageable tasks, selects the appropriate database collections, and evaluates its own answers (Critic Node) to ensure high accuracy.
*   **Advanced Semantic Search:** Uses a local **Qdrant** Vector Database with metadata filtering capabilities to retrieve specific information about professors, international mobility, degree programs, and department news.
*   **Structured Outputs:** Leverages Pydantic to force the LLM to output strictly formatted JSON for tool selection and query reformulation.
*   **Degree Grade Calculator:** A built-in Gradio tool that simulates the final degree grade based on the student's current GPA and department regulations.
*   **Privacy & Local Execution:** Runs entirely locally using **Ollama** (`qwen3:14b`), ensuring zero data leakage.

## 🛠️ Tech Stack

*   **Frameworks:** LangChain, LangGraph
*   **LLM:** Ollama (Qwen3:14b)
*   **Embeddings:** HuggingFace (`BAAI/bge-m3`)
*   **Vector Database:** Qdrant
*   **Reranking:** FlashRank
*   **User Interface:** Gradio

## 📂 Project Structure

```text
diem-virtual-assistant/
├── notebooks/
│   └── chatbot.ipynb          # Main application file (Agent logic + Gradio UI)
├── metadata_manifest/         # JSON files defining metadata rules for the LLM
│   ├── manifest_docenti.json
│   ├── manifest_bandi.json
│   └── ...
├── qdrant_db/                 # (Excluded from repo) Local Vector DB folder
├── .gitignore                 # Specifies intentionally untracked files
└── README.md
