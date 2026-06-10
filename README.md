# Local LLM Document Converter

A small Flask app that uses a local Ollama server as a document conversion engine.

Supported uploads include text-like files, PDF, DOCX, and XLSX. PDF, DOCX, and XLSX files are extracted into text first, then sent to the selected local model for conversion.

## Requirements

- Python 3.10+
- Ollama running at `http://localhost:11434`
- At least one pulled Ollama model, for example:

```bash
ollama pull llama3.1
```

## Run

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python app.py
```

Open `http://127.0.0.1:5000`.

## Configuration

- `OLLAMA_BASE_URL`: defaults to `http://localhost:11434`
- `OLLAMA_TIMEOUT`: defaults to `300` seconds
- `OLLAMA_NUM_PREDICT`: defaults to `2048` output tokens
- `FLASK_PORT`: defaults to `5000`
- `MAX_UPLOAD_BYTES`: defaults to `5242880`

The app reads available models from Ollama's `/api/tags` endpoint and sends conversion prompts to `/api/generate`.

If Ollama times out on generation, try a smaller/faster model, a smaller document, or a longer timeout:

```bash
OLLAMA_TIMEOUT=900 OLLAMA_NUM_PREDICT=1024 python app.py
```
