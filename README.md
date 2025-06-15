# LangChain PDF Question Answering with Pinecone & OpenAI

This project demonstrates how to build a question-answering system over a collection of PDF documents using [LangChain](https://python.langchain.com/), [OpenAI Embeddings](https://platform.openai.com/docs/guides/embeddings), and [Pinecone Vector Database](https://www.pinecone.io/).

## Features

- **Automatic PDF loading:** Reads all PDFs from a specified folder.
- **Text chunking:** Splits documents into manageable chunks for better embedding and retrieval.
- **Semantic search:** Uses OpenAI embeddings and Pinecone for fast, relevant document retrieval.
- **Question answering:** Answers natural language questions using retrieved document content and OpenAI LLMs.

---

## Project Structure

```
langchain/
├── test.ipynb
├── .env
├── requirements.txt
└── (your PDF files)
```

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/rdshyamvijay/LangChain-RAG-OpenAI-PDFQA.git
cd <your-repo>
```

### 2. Install Dependencies

It’s recommended to use a virtual environment.

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

**Example `requirements.txt`:**
```
langchain
openai
pinecone-client
python-dotenv
```

### 3. Set Up Environment Variables

Create a `.env` file in the project root with your API keys:

```
OPENAI_API_KEY=your-openai-api-key
PINECONE_API_KEY=your-pinecone-api-key
```

### 4. Add Your PDF Files

Place your PDF files in a folder (e.g., `./pdfs/`).  
Update the `DATA_DIR` variable in the notebook to point to this folder.

---

## Usage

1. **Open `test.ipynb` in VS Code or Jupyter Notebook.**
2. **Set the `DATA_DIR` variable** to the path where your PDFs are stored.
3. **Run all cells** in order.

Example query:
```python
our_query = "How many jobs have been saved during the pandemic?"
answer = retrieve_answers(our_query)
print(answer)
```

---

## How It Works

1. **Load PDFs:**  
   All PDFs in the specified folder are loaded and parsed.

2. **Chunk Text:**  
   Documents are split into smaller chunks for better embedding and retrieval.

3. **Embed Chunks:**  
   Each chunk is converted to a vector using OpenAI embeddings.

4. **Store in Pinecone:**  
   Vectors are stored in a Pinecone index for fast similarity search.

5. **Ask Questions:**  
   User queries are embedded, similar chunks are retrieved, and an LLM generates an answer.

---

## Customization

- **Change chunk size/overlap:**  
  Adjust parameters in `chunk_data()` for different chunking strategies.
- **Switch LLMs or embeddings:**  
  Swap out OpenAI for other providers supported by LangChain.
- **Add more file types:**  
  Use other LangChain loaders for TXT, DOCX, etc.

---

## Troubleshooting

- **API Key Errors:**  
  Make sure your `.env` file is set up and loaded.
- **Pinecone Errors:**  
  Ensure your Pinecone environment and index parameters match your account settings.
- **PDF Parsing Issues:**  
  Some PDFs may not parse cleanly; check the output of `doc` for issues.

---

## References

- [LangChain Documentation](https://python.langchain.com/)
- [OpenAI Embeddings](https://platform.openai.com/docs/guides/embeddings)
- [Pinecone Docs](https://docs.pinecone.io/)

---

## License

MIT License

---

## Author

Shyam(https://github.com/rdshyamvijay)
