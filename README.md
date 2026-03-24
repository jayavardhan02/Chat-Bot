# PDF Question Answering using LangChain, Ollama and ChromaDB

This project allows users to ask **natural language questions directly from a PDF document** using **LangChain, Ollama, and ChromaDB**.

The system automatically reads the PDF, splits it into smaller chunks, converts them into embeddings locally, stores them in a vector database, and answers questions using a local large language model.

The entire pipeline runs **locally and privately without external API calls**.

---

## Project Structure

pdf-qa-ollama/

data/
    doc.pdf — Input PDF document

db/
    Chroma vector database (auto-generated)

main.py — Main execution script
requirements.txt — Python dependencies
README.md — Project documentation

---

## Features

* Load and process PDF documents using **PyPDFLoader**
* Split documents into semantic text chunks
* Generate embeddings locally using **Ollama embeddings**
* Store vector embeddings using **ChromaDB**
* Retrieve relevant document chunks for answering questions
* Generate answers using a **local LLM**
* Fully **offline and privacy-friendly**

---

## Requirements

* Python 3.10 or higher
* Ollama installed and running
* Optional: Docker (for containerized Ollama)

### Required Python Libraries

langchain_community
langchain_text_splitters
langchain_ollama
langchain_chroma

Install all dependencies using:

pip install -r requirements.txt

---

## How It Works

### 1. PDF Loading

The **PyPDFLoader** extracts text and metadata from the input PDF document.

### 2. Text Splitting

The **RecursiveCharacterTextSplitter** divides the document into smaller overlapping chunks for efficient retrieval.

### 3. Embedding and Storage

Each text chunk is converted into vector embeddings using the **nomic-embed-text model** and stored in a **ChromaDB vector database**.

### 4. Question Answering

When a user asks a question, the retriever finds the most relevant chunks and the **Llama 3.2 model** generates the final answer.

---

## Usage

1. Place your PDF document inside the **data** folder.

2. Update the PDF path in **main.py**

pdf_file = r"data/doc.pdf"

3. Run the script

python main.py

4. Type your question when prompted.

### Example

Ingested 42 chunks into db

Ask a question about the PDF:
What is the main topic of the document?

Answer:
The report focuses on the impact of AI in healthcare innovation.

---

## Configuration

You can modify these parameters inside **main.py**:

chunk_size = 1200
chunk_overlap = 200

Embedding model: nomic-embed-text
LLM model: llama3.2:3b

---

## Models Used

Embeddings Model
nomic-embed-text

Language Model
llama3.2:3b

---

## Future Enhancements

* Add a **web interface using Streamlit or FastAPI**
* Support **multiple PDF document ingestion**
* Implement **automatic document summarization**
* Add **citation and source tracking for answers**

---

## Author

Developed by
Manchala Jayavardhan
