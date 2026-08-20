# 🛡️ RZai — Enterprise Private Document Intelligence & RAG Platform

![License](https://img.shields.io/badge/license-MIT-green.svg)
![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg)
![Streamlit](https://img.shields.io/badge/framework-Streamlit-FF4B4B.svg)
![Ollama](https://img.shields.io/badge/LLM-Ollama%20%2F%20Llama3-000000.svg)

**RZai** is a modern, high-performance **Retrieval-Augmented Generation (RAG)** platform engineered to extract actionable insights from complex PDF documents, legal contracts, and technical manuals with **100% data privacy and zero API overhead**.

Powered by local open-weight Large Language Models via **Ollama**, local vector embeddings, and an intuitive Cyber-SaaS interface, RZai enables organizations and individuals to chat with their documents completely offline.

---

## ✨ Key Features

* 🔒 **100% On-Device & Privacy-Preserving:** No data ever leaves your machine. Your sensitive PDF contents are processed locally without third-party cloud dependencies or external API calls.
* 💸 **Zero Operating Cost:** Operates indefinitely for free with open-source models—no credit card, API key, or subscription required.
* ⚡ **High-Precision Semantic Retrieval:** Integrates **ChromaDB** with **HuggingFace MiniLM** embeddings to perform fast, accurate document segmentation and context extraction.
* 🎨 **Cyber-SaaS Dashboard:** Clean, responsive, and dark-themed interface built using Streamlit and custom CSS styling.
* 🚀 **Seamless Model Integration:** Native support for local open-weights LLMs like `llama3`, `mistral`, or `qwen` via Ollama.

---

## 🏗️ Architecture Overview
[User Upload: PDF]
│
▼
[PyPDF Document Loader] ──► [Recursive Text Splitter]
│
▼
[HuggingFace Embeddings] ──► [Chroma Vector Store]
│
▼
[User Query] ─────────────► [Context Retrieval (Top-K)]
│
▼
[Ollama Local LLM] ◄─────── [Prompt Formulation]
│
▼
[Streamlit Cyber-UI Response]
1. **Document Ingestion:** The uploaded PDF is parsed and dynamically split into optimized text chunks using `RecursiveCharacterTextSplitter`.
2. **Vector Indexing:** Dense vector representations are computed via `all-MiniLM-L6-v2` and cached in an in-memory `Chroma` vector database.
3. **Contextual Retrieval:** User queries undergo semantic similarity search to retrieve the most relevant context blocks.
4. **Local Generation:** The compiled prompt (Context + Query) is executed through **Ollama**'s locally hosted LLM endpoint.

---

## 🚀 Quick Start Guide

### Prerequisites

1. Install [Ollama](https://ollama.com/) on your machine.
2. Pull your preferred model (e.g., Llama 3) via terminal:
   ```bash
   ollama pull llama3
   Ensure Python 3.10+ is installed on your system.
   Create and Activate a Virtual Environment (Optional but Recommended):

Bash
# On macOS/Linux
python3 -m venv venv
source venv/bin/activate

# On Windows
python -m venv venv
venv\Scripts\activate
Install Dependencies:

Bash
pip install -r requirements.txt
Launch the Platform:

Bash
streamlit run app.py
🛠️ Technology StackComponentTechnology
/ LibraryFrontend / UIStreamlit (Custom CSS Dark Theme)LLM ExecutionOllama (llama3)
EmbeddingsHuggingFace Transformers (all-MiniLM-L6-v2)Vector DatabaseChromaDB (langchain-chroma)
Framework & RAGLangChain Core & CommunityPDF ProcessingPyPDF
⚙️ Configuration & Customization
Change LLM Model: To switch to another model (e.g., mistral or qwen2), pull the model using Ollama (ollama pull mistral) and update line 83 in app.py:

Python
llm = Ollama(model="mistral")
Chunk Size Adjustments: Modify document chunking inside app.py under the RecursiveCharacterTextSplitter parameters:

Python
text_splitter = RecursiveCharacterTextSplitter(chunk_size=500, chunk_overlap=50
📜 License
Distributed under the MIT License. See LICENSE for more information.
rag ollama streamlit pdf-analysis langchain chromadb python local-ai llama3 document-intelligence
