# 🤖 RAG EdTech Assistant

An AI-powered educational assistant built using **Retrieval-Augmented Generation (RAG)** to answer user questions from a curated knowledge base of educational content.

The system retrieves relevant information from documents and uses a Large Language Model (LLM) to generate context-aware responses, reducing reliance on the model's general knowledge.

---

## 📌 Project Overview

The **RAG EdTech Assistant** is a Generative AI application designed to help students and learners interact with educational content using natural language.

Instead of asking an LLM to answer questions only from its pretrained knowledge, the application first retrieves relevant information from a custom knowledge base and then provides that context to the LLM.

### Core Pipeline

```text
User Question
      ↓
Query Processing
      ↓
Vector Similarity Search
      ↓
Relevant Documents / Chunks
      ↓
Context Construction
      ↓
Large Language Model
      ↓
Generated Answer
```

---

## 🎯 Problem Statement

Educational information is often distributed across multiple PDFs, CSV files, webpages, and other resources. Searching through these resources manually can be time-consuming.

This project aims to provide a conversational interface through which users can ask questions in natural language and receive answers based on the information available in the configured knowledge base.

---

## 💡 Key Features

* 📄 **PDF Knowledge Base**

  * Processes educational content from PDF documents.

* 📊 **CSV Knowledge Base**

  * Supports structured information stored in CSV files.

* 🌐 **URL-Based Knowledge**

  * Allows information from configured web resources to be incorporated into the knowledge base.

* ✂️ **Document Chunking**

  * Splits large documents into smaller chunks suitable for retrieval.

* 🔢 **Text Embeddings**

  * Converts text into numerical vector representations for semantic search.

* 🗄️ **Vector Database**

  * Uses ChromaDB for storing and retrieving document embeddings.

* 🔎 **Semantic Retrieval**

  * Retrieves relevant knowledge based on the meaning of the user's query.

* 🧠 **LLM-Based Answer Generation**

  * Uses a Large Language Model to generate responses using retrieved context.

* 🔗 **RAG Architecture**

  * Combines information retrieval with generative AI.

* 🔐 **Environment-Based API Configuration**

  * API credentials are kept outside the source code using environment variables.

---

## 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │    Knowledge Base    │
                    │                      │
                    │ PDF │ CSV │ URL Data │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Document Loading   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Text Chunking     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │     Embeddings       │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │      ChromaDB        │
                    │    Vector Store      │
                    └──────────┬───────────┘
                               │
                     User Query
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Semantic Retrieval   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Retrieved Context    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │       LLM            │
                    │   Response Generation│
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │     Final Answer     │
                    └──────────────────────┘
```

---

## 🛠️ Technology Stack

| Category                  | Technologies                   |
| ------------------------- | ------------------------------ |
| Programming Language      | Python                         |
| LLM Application Framework | LangChain                      |
| Vector Database           | ChromaDB                       |
| LLM Provider              | Groq                           |
| Generative AI             | Large Language Models          |
| Retrieval                 | Semantic / Vector Search       |
| Data Sources              | PDF, CSV, URL                  |
| Environment Management    | `.env` / Environment Variables |
| Development               | Jupyter Notebook, VS Code      |
| Version Control           | Git / GitHub                   |

> Update this table if your implementation uses a different embedding model, document loader, framework, or application framework.

---

## 📂 Project Structure

```text
RAG-EdTech-Assistant/
│
├── 📁 data/
│   ├── pdf/
│   └── csv/
│
├── 📁 notebooks/
│   └── experiments.ipynb
│
├── 📁 src/
│   ├── document_loader.py
│   ├── text_splitter.py
│   ├── embeddings.py
│   ├── vector_store.py
│   ├── retriever.py
│   └── llm.py
│
├── 📁 screenshots/
│   └── chatbot-demo.png
│
├── app.py
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

> Keep only folders and files that actually exist in your repository. Do not create or claim files that are not part of your implementation.

---

## ⚙️ How RAG Works in This Project

### 1. Document Ingestion

Educational information is collected from supported sources such as PDFs, CSV files, and configured URLs.

### 2. Text Extraction

The content is extracted from the source documents and converted into processable text.

### 3. Text Chunking

Large documents are divided into smaller chunks.

Chunking helps the retrieval system identify focused pieces of information instead of processing an entire document at once.

### 4. Embedding Generation

The text chunks are converted into vector representations using an embedding model.

Similar pieces of text are represented by vectors that are closer in the embedding space.

### 5. Vector Storage

The generated embeddings and their associated text are stored in **ChromaDB**.

### 6. Query Processing

When a user asks a question, the question is converted into an embedding.

### 7. Semantic Retrieval

The system searches the vector database and retrieves the most relevant chunks of information.

### 8. Context Construction

The retrieved information is provided as context to the LLM.

### 9. Response Generation

The LLM generates a response using the retrieved context.

---

## 🔄 Example Workflow

### User Query

```text
What topics are covered in the Machine Learning module?
```

### Retrieval

The system searches the vector database for relevant educational content.

### Retrieved Context

```text
Relevant content retrieved from the configured knowledge base...
```

### LLM

The retrieved context is passed to the language model.

### Final Response

```text
The Machine Learning module covers the topics available
in the retrieved educational material...
```

The exact response depends on the documents available in the knowledge base.

---

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/ManasiKOLHAL/RAG-EdTech-Assistant.git
```

### 2. Navigate to the project

```bash
cd RAG-EdTech-Assistant
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

### 4. Activate the environment on Windows

```bash
venv\Scripts\activate
```

### 5. Install dependencies

```bash
pip install -r requirements.txt
```

---

## 🔑 Environment Configuration

Create a `.env` file in the project root.

```text
GROQ_API_KEY=your_api_key_here
```

For portfolio repositories, create a `.env.example` file instead:

```text
GROQ_API_KEY=your_groq_api_key
```

The actual `.env` file should be included in `.gitignore`.

---

## ▶️ Running the Application

Use the actual entry-point command for your project.

For example:

```bash
python app.py
```

If your project uses a different entry point, replace the command above with the command required by your implementation.

---

## 📦 Requirements

The project dependencies are listed in:

```text
requirements.txt
```

Install them using:

```bash
pip install -r requirements.txt
```

---


### Example

```text
User Question
      ↓
Retrieved Educational Context
      ↓
LLM Processing
      ↓
AI Generated Answer
```

---

## 📊 Evaluation

The project can be evaluated using retrieval and generation quality metrics such as:

* Retrieval relevance
* Context relevance
* Answer relevance
* Faithfulness / groundedness
* Response latency
* Retrieval accuracy

If you have measured these metrics, add your **actual results** here.

Example:

| Metric             |           Result |
| ------------------ | ---------------: |
| Retrieval Accuracy | Add actual value |
| Answer Relevance   | Add actual value |
| Response Time      | Add actual value |

Do not report estimated or unmeasured values as project results.

---

## ⚠️ Limitations

* The quality of generated responses depends on the quality of the knowledge base.
* Incorrect or incomplete source documents can lead to incomplete answers.
* Retrieval quality depends on chunking, embeddings, and search configuration.
* LLM-generated responses may still contain inaccuracies.
* API availability and rate limits may affect application usage.

---

## 🔮 Future Improvements

* [ ] Add source citations to generated answers
* [ ] Add retrieval evaluation
* [ ] Add response faithfulness evaluation
* [ ] Implement conversation memory
* [ ] Improve chunking strategies
* [ ] Experiment with different embedding models
* [ ] Add reranking
* [ ] Add automated tests
* [ ] Add production logging and monitoring
* [ ] Deploy the application
* [ ] Add authentication if required
* [ ] Optimize retrieval latency

---

## 🎓 Learning Outcomes

Through this project, I gained practical experience with:

* Retrieval-Augmented Generation
* Large Language Models
* LangChain
* Vector databases
* Semantic search
* Text embeddings
* Document processing
* Prompt engineering
* Generative AI application development
* API integration
* Environment-variable management
* AI application architecture

---

## 👩‍💻 Author

**Manasi Kolhal**

B.E. Electronics & Telecommunication Engineering

### GitHub

https://github.com/ManasiKOLHAL

### LinkedIn

www.linkedin.com/in/manasi-kolhal

---

## ⭐ Acknowledgements

This project was developed as part of my learning and practical work in **Artificial Intelligence, Generative AI, and Machine Learning**.
