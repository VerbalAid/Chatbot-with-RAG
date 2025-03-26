# RAGChat: A Retrieval Augmented Generation Chatbot

RAGChat is a chatbot application that leverages Retrieval Augmented Generation (RAG) by processing PDF documents, creating a vector store from their content, and then using a language model to generate context-aware responses. All the code is contained in a single file for simplicity.

---

## Features

- **Document Ingestion:** Automatically loads and processes PDFs from a designated folder.
- **Vector Store Creation:** Uses Chroma to build a vector database from document chunks.
- **Retrieval Augmented Generation:** Retrieves relevant document sections to generate responses.
- **Chat Interface:** Provides a user-friendly Gradio web interface.
- **Flexible LLM Integration:** Option to use OpenAI’s GPT models or switch to a free/open-source language model.

---

## Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/RAGChat.git
cd RAGChat
2. Create and Activate a Virtual Environment (Optional but Recommended)
bash
Copy
Edit
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
3. Install Required Libraries
Run the following command in your terminal:

bash
Copy
Edit
pip install langchain_community langchain_text_splitters langchain_openai langchain_chroma gradio python-dotenv pypdf
Note: The installation command is also included in the code for reference.

4. Set Up Environment Variables
Create a .env file in the root of the repository with the following content:

env
Copy
Edit
OPENAI_API_KEY=your_openai_api_key_here
Replace your_openai_api_key_here with your actual API key. If you choose to use a free or local LLM, adjust the code accordingly.

Usage
Since all the code is in a single file, running the chatbot is straightforward. Simply execute the script:

bash
Copy
Edit
python your_script_name.py
When executed, the script launches a Gradio web interface in your browser. Use the interface to ask questions and receive responses generated by the language model based on the retrieved document context.

Switching to a Free LLM
If you prefer not to use OpenAI’s API, you can switch to a free, open-source language model. For example, you can use Hugging Face Transformers:

1. Install Hugging Face Transformers
bash
Copy
Edit
pip install transformers
2. Modify the Code
Replace the OpenAI LLM instantiation with a free model:

python
Copy
Edit
# Original:
# llm = ChatOpenAI(temperature=0.5, model='gpt-4o-mini')

# With a free model example:
from transformers import pipeline
from langchain.llms import HuggingFacePipeline

pipe = pipeline("text-generation", model="gpt2", tokenizer="gpt2")
llm = HuggingFacePipeline(pipeline=pipe)
Adjust the rest of the code as needed to ensure compatibility with the free model.

Project Structure
For simplicity, all the code is kept in one file within this repository. As the project grows, consider refactoring into multiple modules for better organization and maintainability.

bash
Copy
Edit
RAGChat/
├── data/                  # Directory containing PDF documents
├── chroma_db/             # Directory for the Chroma vector store
├── your_script_name.py    # Main script containing all the code
├── .env                   # Environment variables file
└── README.md              # Project documentation (this file)
Contributing
Feedback and contributions are welcome. If you encounter any issues or have suggestions for improvements, please open an issue or submit a pull request.

License
This project is licensed under the MIT License. See the LICENSE file for details.
