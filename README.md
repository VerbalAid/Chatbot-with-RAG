## Overview

This chatbot processes PDF documents, splits them into manageable chunks, and stores these chunks as vector embeddings in a ChromaDB database. When you ask questions, it retrieves the most relevant chunks and uses them to inform the AI's response, ensuring answers are grounded in your documents rather than the model's general knowledge.

## Features

- Load and process PDFs from a directory
- Split documents into optimized chunks
- Store text embeddings in ChromaDB vector database
- Retrieve relevant document sections based on queries
- Generate contextually accurate responses using OpenAI models
- Interactive Gradio web interface

## Prerequisites

- Python 3.8+
- OpenAI API key

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/pdf-rag-chatbot.git
   cd pdf-rag-chatbot
   ```

2. Install the required packages:
   ```bash
   pip install langchain_community langchain_text_splitters langchain_openai langchain_chroma gradio python-dotenv pypdf
   ```

3. Create a `.env` file in the root directory and add your OpenAI API key:
   ```
   OPENAI_API_KEY=your_openai_api_key_here
   ```

## Usage

1. Place your PDF files in a directory named `data` in the project root.

2. Run the document processing script to create your vector database:
   ```python
   python process_docs.py
   ```

3. Launch the chatbot:
   ```python
   python chatbot.py
   ```

4. Access the web interface (typically at http://127.0.0.1:7860) and start asking questions about your PDFs!

## How It Works

1. **Document Processing**: PDFs are loaded and split into chunks of 300 characters with 100 character overlap
2. **Embedding Generation**: Text chunks are converted to embeddings using OpenAI's text-embedding-3-large model
3. **Vector Storage**: Embeddings are stored in ChromaDB with unique UUIDs
4. **Retrieval**: When a question is asked, the system finds the 5 most relevant chunks
5. **Response Generation**: OpenAI's GPT-4o-mini generates responses based on the retrieved context

## Project Structure

```
pdf-rag-chatbot/
├── data/                  # Place your PDF files here
├── chroma_db/             # Vector database storage
├── process_docs.py        # Document processing and database creation
├── chatbot.py             # Gradio interface and chatbot logic
└── README.md              # Project documentation
```

## License

[Your chosen license]

## Acknowledgments

- LangChain for document processing and embedding generation
- OpenAI for embedding and language models
- ChromaDB for vector storage
- Gradio for the web interface
```

