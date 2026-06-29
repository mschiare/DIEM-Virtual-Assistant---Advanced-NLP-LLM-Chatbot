# 🎓 DIEM Virtual Assistant - Advanced NLP & LLM Chatbot

An intelligent conversational agent built to assist students and users with information regarding the **DIEM Department** (Dipartimento di Ingegneria dell'Informazione ed Elettrica e Matematica Applicata) at the University of Salerno. 

This project was developed as part of my Master's Degree in Computer Engineering for Artificial Intelligence. It demonstrates the practical application of **Large Language Models (LLMs)**, **Retrieval-Augmented Generation (RAG)**, and **Agentic Workflows**.

## 🚀 Features

* **Agentic Workflow (Plan-and-Execute):** Built with LangGraph, the chatbot analyzes the user's intent, breaks down complex queries into manageable tasks, selects the appropriate database collections, and evaluates its own answers (Critic Node) to ensure high accuracy.
* **Advanced Semantic Search:** Uses a local **Qdrant** Vector Database with metadata filtering capabilities to retrieve specific information about professors, international mobility, degree programs, and department news.
* **Structured Outputs:** Leverages Pydantic to force the LLM to output strictly formatted JSON for tool selection and query reformulation.
* **Degree Grade Calculator:** A built-in Gradio tool that simulates the final degree grade based on the student's current GPA and department regulations.
* **Privacy & Local Execution:** Runs entirely locally using **Ollama** (`qwen3:14b`), ensuring zero data leakage.

## 🛠️ Tech Stack

* **Frameworks:** LangChain, LangGraph
* **LLM:** Ollama (Qwen3:14b)
* **Embeddings:** HuggingFace (`BAAI/bge-m3`)
* **Vector Database:** Qdrant
* **Reranking:** FlashRank
* **User Interface:** Gradio

## ⚠️ Repository Scope (Note on Data)

> **Note:** This repository focuses exclusively on the **Inference Engine** and the **User Interface**. 
> The modules related to web scraping, data chunking, and the generation of the Qdrant Vector Database have been intentionally omitted to keep the repository lightweight and to protect the department's raw scraped data. The code provided here assumes the existence of a pre-populated `qdrant_db` folder.

## 📂 Project Structure

```text
diem-virtual-assistant/
├── metadata_manifest/         # JSON files defining metadata rules for the LLM
│   ├── manifest_docenti.json
│   ├── manifest_bandi.json
│   └── ...
├── notebooks/
│   └── chatbot.ipynb          # Main application file (Agent logic + Gradio UI)
├── qdrant_db/                 # Local Vector DB folder
├── .gitignore                 # Specifies intentionally untracked files
└── README.md
```

## ⚙️ Setup and Installation

Follow these steps to configure and run the virtual assistant locally on your machine.

### 1. Clone the Repository
Clone this repository to your local directory and navigate into the project folder:
```bash
git clone https://github.com/mschiare/DIEM-Virtual-Assistant---Advanced-NLP-LLM-Chatbot.git

cd DIEM-Virtual-Assistant---Advanced-NLP-LLM-Chatbot
```

### 2. Download the Pre-built Vector Database
The repository does not include the vector database files.
After cloning the repository, download the pre-built `qdrant_db.zip`
from the Releases section and extract it into the project root directory.

1. Go to the [Releases page](https://github.com/mschiare/DIEM-Virtual-Assistant---Advanced-NLP-LLM-Chatbot/releases/tag/v1.0).
2. Download the latest `qdrant_db.zip` file.
3. Extract the contents into the project root directory, so that the `qdrant_db/` folder is at the same level as the `notebooks/` folder.

### 3. Prepare the Directory Structure
Your root folder must look like this:
* `metadata_manifest/` (contains your JSON configuration files)
* `notebooks/` (contains `chatbot.ipynb`)
* `qdrant_db/` (contains your local vector database files)

### 4. Create and Activate a Virtual Environment
It is highly recommended to isolate the project dependencies using a virtual environment:
```bash
# Create the environment
python3 -m venv chatbot_env

# Activate it (Mac/Linux)
source chatbot_env/bin/activate

# Activate it (Windows)
chatbot_env\Scripts\activate
```

### 5. Install Dependencies
Install all the required frameworks, including LangChain, LangGraph, Gradio, and Qdrant drivers:
```bash
pip install -r requirements.txt
```

### 6. Install and Run Ollama
The architecture relies entirely on local model execution via Ollama. 
1. Download and install Ollama from [ollama.com](https://ollama.com/).
2. Pull the **Qwen3 14B** model by running the following command in your terminal:
```bash
ollama run qwen3:14b
```
Keep the Ollama application running in the background.

### 7. Launch the Assistant
Open the main application notebook and execute the cells to start the web interface:
```bash
jupyter notebook notebooks/chatbot.ipynb
```
Once the cells are executed, Gradio will generate a local URL (e.g., `http://127.0.0.1:7860`). Open it in your browser to interact with the chatbot!

---

## 🤖 System Architecture & Flow

The chatbot is built using an **Agentic Workflow** driven by **LangGraph**. When a query enters the system, it goes through a coordinated multi-node routing system:

1. **Planner / Classifier Node:** The input query is analyzed, reformulated for better semantic retrieval, and classified into one of the specialized manifest categories.
2. **Retrieval & Reranking Node:** Relevant contexts are extracted from the local **Qdrant** collection using metadata filters. The retrieved documents are then filtered through **FlashRank** to select only the top relevant chunks.
3. **Synthesis Node:** The local `qwen3:14b` model processes the context and the user query to build a comprehensive answer.
4. **Critic Node:** A dedicated evaluation guardrail checks the answer for hallucinations, factual accuracy, and completeness before returning it to the user.

---

## 👩‍💻 Author

Developed by **[Your Name]** Master's Degree Candidate in Computer Engineering for Artificial Intelligence  
*Università degli Studi di Salerno (UNISA)* * **Focus:** Natural Language Processing (NLP), Large Language Models (LLMs), Machine Learning, AI for Cybersecurity.
* **LinkedIn:** [Your LinkedIn Profile Link](#)
* **GitHub:** [https://github.com/YOUR-USERNAME](https://github.com/YOUR-USERNAME)
