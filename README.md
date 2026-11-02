# Literature Review Comparison Tool

Streamlit app that compares up to 5 research papers (methods, findings, limitations) using Claude.

## Workflow
```mermaid
flowchart LR
    A[Paste / upload 5 papers] --> B[Stage 1: Ingestion & sanitization]
    B --> C[Stage 2: LLM extraction, prompt v3]
    C --> D[Stage 3: Matrix synthesis]
    D --> E[(SQLite log)]
    D --> F[DataFrame + CSV download]
```

## Setup (macOS)
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
export ANTHROPIC_API_KEY="your-key"
streamlit run app.py
```
Opens at http://localhost:8501.

## Usage
1. Paste text or upload `.txt`/`.pdf` in each Paper tab (minimum 2 papers, 200+ characters each).
2. Click **Generate Matrix**.
3. View the matrix, download CSV, or open **Run history**.

## Data storage
Every run is logged to `literature_review.db` (table `runs`: timestamp, sanitized inputs, matrix, errors).

## Files
- `app.py`: application
- `prompts.md`: v1 to v3 prompt iterations (v3 in use)
- `test_evidence.md`: test cases
- `requirements.txt`: dependencies
