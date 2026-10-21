# Hallucination-Aware RAG

A Streamlit application that performs Retrieval-Augmented Generation (RAG) while actively detecting and mitigating AI hallucinations.

## Features
- **Multi-source Support:** Upload PDF, TXT, DOCX files, or provide web URLs.
- **RAG Pipeline:** Utilizes Llama 3.1 8B Instruct model via Hugging Face Inference API for generation, and local sentence-transformers for fast retrieval.
- **Hallucination Detection:** Uses a local NLI (Natural Language Inference) cross-encoder model to verify the LLM's claims against the retrieved context.
- **Interactive UI:** A user-friendly Streamlit dashboard that visualizes the Hallucination Score using a gauge chart, provides a claim-by-claim breakdown, and offers a corrected answer if hallucinations are detected.

## Tech Stack
- **UI:** [Streamlit](https://streamlit.io/), [Plotly](https://plotly.com/python/)
- **LLM / Generation:** `meta-llama/Llama-3.1-8B-Instruct` (via Hugging Face Hub)
- **Embeddings / Retrieval:** `sentence-transformers/all-MiniLM-L6-v2`, FAISS
- **NLI / Verification:** `cross-encoder/nli-MiniLM2-L6-H768`
- **Document Parsing:** `pypdf`, `python-docx`, `beautifulsoup4`

## Setup

1. **Clone or download** this repository.
2. **Install the dependencies**:
   It is recommended to use a virtual environment.
   ```bash
   pip install -r requirements.txt
   ```
3. **Configure the API Key**:
   Open `config.py` and replace the `HF_API_KEY` with your own Hugging Face API key.
   ```python
   HF_API_KEY = "your_huggingface_api_key_here"
   ```

## Usage

Run the Streamlit application:
```bash
streamlit run app.py
```

1. **Add Your Sources:** Upload files (PDF, TXT, DOCX) or paste a URL in the sidebar/upload section.
2. **Ask a Question:** Ask a question related to the uploaded documents.
3. **Analyze Results:** Review the generated answer, the hallucination score, claim-by-claim verification, and the corrected answer if hallucinations are found!

