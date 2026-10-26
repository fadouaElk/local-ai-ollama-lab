# FSTT Local AI Assistant

A fully local assistant: Flask web UI → Ollama → local LLM, with a keyword (TF-IDF) retriever over `documents/`,
conversation history, structured (JSON) answers and response-time display.

Tested on Ubuntu, 16 GB RAM, no dedicated GPU (Ollama in CPU-only mode).

## Setup
```bash
ollama pull qwen3.5:4b
ollama pull gemma3:4b
pip install flask requests psutil pandas
```

## Run
```bash
cd source
MODEL=qwen3.5:4b python app.py   # http://127.0.0.1:5001
python chatbot.py                # console chatbot
python benchmark.py qwen3.5:4b gemma3:4b
```
Environment variables: `MODEL` (default model of the web app), `OLLAMA_URL`, `PORT`.

## Notes
- The 4-billion-parameter models (`qwen3.5:4b`, `gemma3:4b`, Q4_K_M) were chosen to fit a laptop without GPU.
- The thinking mode is disabled (`think: False`) in the web app to reduce response times on CPU.
- The server is bound to `127.0.0.1` only (no network exposure).