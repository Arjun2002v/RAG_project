# RAG_project

A local, fully offline Retrieval-Augmented Generation (RAG) pipeline. No API
keys, no cloud services — everything runs on your machine via [Ollama](https://ollama.com)
for both the LLM and embeddings, with [Chroma](https://www.trychroma.com/) as
the vector store.

## Stack

| Component  | Choice                          |
| ---------- | -------------------------------- |
| LLM        | Ollama (`llama3.2` or `gemma3`) |
| Embeddings | Ollama (`nomic-embed-text`)     |
| Vector DB  | Chroma (local, file-based)      |
| Framework  | LangChain                        |

## Prerequisites

- Python 3.10+
- [Ollama](https://ollama.com) installed and running

Pull the models used by this project:

```bash
ollama pull llama3.2
ollama pull nomic-embed-text
```

## Setup

```bash
python -m venv .venv
source .venv/Scripts/activate   # Windows (Git Bash); use .venv\Scripts\Activate.ps1 for PowerShell
pip install -r requirements.txt
```

## Project layout

```
data/         # put source documents here (PDF, TXT, MD, ...) — see data/README.md
chroma_db/    # persisted vector store (created automatically, gitignored)
requirements.txt
```

## Notes

- `chroma_db/` and everything in `data/` (except its README) are gitignored —
  indexed content and the vector store stay local.
- Swap `llama3.2` for any other Ollama model (e.g. `gemma3`) by changing the
  model name where the LLM is instantiated.
