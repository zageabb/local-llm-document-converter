# Local LLM Document Converter

Created a Flask app in the workspace that connects to Ollama at `http://localhost:11434`, lists available models, and converts pasted or uploaded documents.

Supported uploads include text-like files, PDF, DOCX, and XLSX.

Run it from the project folder:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python app.py
```

Then open `http://127.0.0.1:5000`.

Set `OLLAMA_TIMEOUT=600` before running if your local model needs a longer first-load window.
