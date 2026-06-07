# What is RAG? 📚

A practical guide and implementation of **Retrieval-Augmented Generation (RAG)** - a technique that combines large language models with external knowledge retrieval to provide more accurate, grounded, and contextual responses.

## Overview

This project demonstrates how to build RAG systems by:
- **Extracting** knowledge from documents (PDFs, text files, etc.)
- **Processing** and structuring that knowledge
- **Retrieving** relevant information based on queries
- **Generating** enhanced responses using both retrieved knowledge and LLMs

## What is RAG?

RAG is a machine learning approach that enhances large language models (LLMs) by retrieving relevant information from external documents before generating responses. This solves common LLM limitations:

- ✅ Provides current, factual information
- ✅ Reduces hallucinations and misinformation
- ✅ Enables domain-specific knowledge integration
- ✅ Improves transparency by citing sources
- ✅ Works with private/proprietary documents

## Project Structure

```
what-is-rag/
├── README.md                          # This file
├── requirements.txt                   # Project dependencies
├── pyproject.toml                     # Project configuration
├── main.py                            # Main application entry point
└── 1_document_loaders/                # Document loading notebooks
    └── pdf_loader.ipynb               # PDF extraction & parsing examples
```

## Installation

### Prerequisites
- Python 3.12+
- pip or your preferred package manager

### Setup

1. **Clone or download the project**
```bash
cd what-is-rag
```

2. **Create a virtual environment** (recommended)
```bash
python -m venv venv
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

### Optional: OCR Support

For advanced PDF image-text extraction with OCR:

**Windows:**
```bash
choco install tesseract-ocr
```

**macOS:**
```bash
brew install tesseract
```

**Linux:**
```bash
sudo apt-get install tesseract-ocr
```

## Key Components

### 1. Document Loaders (`1_document_loaders/pdf_loader.ipynb`)

Demonstrates multiple approaches to extract text from PDF documents:

- **PyPDFLoader**: Fast, basic PDF text extraction
- **PDFMinerLoader**: Detailed layout-aware extraction
- **TesseractBlobParser**: OCR-based extraction for scanned PDFs with image content

**Features shown:**
- Loading PDF files
- Extracting text and metadata
- Handling PDFs with images
- Processing documents for downstream RAG tasks

## Core Dependencies

| Package | Purpose |
|---------|---------|
| `langchain` | LLM orchestration framework |
| `langchain-community` | Community integrations (loaders, utilities) |
| `pypdf` | PDF parsing and manipulation |
| `pdfminer.six` | Advanced PDF text extraction |
| `pdfplumber` | PDF data extraction tool |
| `pytesseract` / `rapidocr-onnxruntime` | Optical Character Recognition (OCR) |
| `openai` | OpenAI API integration |
| `beautifulsoup4` | HTML/XML parsing |
| `python-dotenv` | Environment variable management |

## Usage

### Running Notebooks

Start Jupyter and explore the examples:

```bash
jupyter notebook
```

Navigate to `1_document_loaders/pdf_loader.ipynb` to see:
- PDF loading techniques
- Text extraction methods
- Image extraction and OCR processing
- Document metadata handling

### Python Script

Run the main application:

```bash
python main.py
```

## Next Steps / Roadmap

This project covers the first critical step of RAG: **Document Loading**. Typical RAG pipeline progression:

1. ✅ **Document Loading** - Extract text from various sources
2. 📋 **Document Chunking** - Split large documents into manageable pieces
3. 🔤 **Embeddings** - Convert text to vector representations
4. 🗄️ **Vector Store** - Store and index embeddings for retrieval
5. 🔍 **Retrieval** - Find relevant documents based on queries
6. 🤖 **Generation** - Use LLMs to synthesize responses from retrieved context

## Example Workflow

```python
from langchain_community.document_loaders.pdf import PyPDFLoader

# Load PDF document
loader = PyPDFLoader("document.pdf")
documents = loader.load()

# Process documents (next steps)
# - Split into chunks
# - Generate embeddings
# - Store in vector database
# - Retrieve relevant chunks for queries
# - Generate answers with LLM context
```

## Configuration

Create a `.env` file for sensitive configuration:

```env
OPENAI_API_KEY=sk-your-key-here
PDF_PATH=path/to/documents
```

Load in your code:

```python
from dotenv import load_dotenv
import os

load_dotenv()
api_key = os.getenv('OPENAI_API_KEY')
```

## Troubleshooting

**PDF Loading Issues:**
- Ensure PDF file paths are correct and file exists
- For image-heavy PDFs, use `extract_images=True` with TesseractBlobParser
- Check that pytesseract is properly configured (see OCR Setup above)

**Import Errors:**
- Use correct import paths: `from langchain_community.document_loaders import PDFMinerLoader`
- Verify all dependencies are installed: `pip list`

**Memory Issues:**
- For large PDFs, process in chunks or use streaming loaders
- Consider batch processing multiple documents

## Resources

- [LangChain Documentation](https://python.langchain.com/)
- [RAG Papers & Research](https://arxiv.org/list/cs.IR/recent)
- [OpenAI API Reference](https://platform.openai.com/docs/api-reference)

## License

This project is open source and available for educational and development purposes.

## Contributing

Contributions are welcome! Please feel free to:
- Add more document loader examples
- Implement vector stores and retrieval
- Add LLM integration examples
- Improve documentation

---

**Happy learning!** 🚀 Explore the notebooks to see RAG in action.
