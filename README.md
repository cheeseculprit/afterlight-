# Afterlight

A private, local memory archive for ordinary objects and the people associated with them. It invites remembrance in the spirit of Día de los Muertos without impersonating the dead. A local open-weight model turns your own words into a short archive label, a reflective line, and a question. You can edit the model's wording, see your original text, export the archive, or delete a record.

## Run

1. Install Ollama and Python 3.10+.
2. Download the model once while online: `ollama pull qwen3:1.7b`.
3. Start Ollama if it is not already running: `ollama serve`.
4. From this directory: `python server.py`.
5. Open `http://127.0.0.1:8765`.

On this Windows machine Ollama 0.40.13 and `qwen3:1.7b` are already installed. If a fresh shell cannot find `ollama`, use `C:\Users\saans\AppData\Local\Programs\Ollama\ollama.exe` (the installer location on this machine). The local server was tested with a real model response. No Python packages or frontend dependencies are required.

After installation and the model download, the app needs no internet connection. It binds to loopback only. Text is sent to the local Ollama API and stored as plain JSON in `data/memories.json`. There is no account, remote database, external font, analytics, or cloud inference call in the app. Local files are not encrypted; other people with access to your computer or backups may read them. The archive is not automatically backed up. Use “Export my archive” for a JSON copy. Deletion removes a record from the current local archive, not from backups or prior exports.

To swap models, first pull a compatible Ollama chat model and set `AFTERLIGHT_MODEL` before starting the server (for example `AFTERLIGHT_MODEL=qwen3:4b python server.py` in bash). `AFTERLIGHT_PORT` changes the port. `OLLAMA_URL` changes the Ollama endpoint; pointing it at a remote endpoint would forfeit the local-only privacy property. The model should support structured JSON output.

## Limitations

The model can invent details despite the prompt. Always review and edit its output; the generated prose is not a historical source. The app saves generated text immediately, so remove or edit a record if it misrepresents your memory. It is not a grief counselor, spirit simulator, or secure encrypted vault. Do not expose the local server to an untrusted network.

## Files

- `server.py`: Python standard-library HTTP server, structured Ollama inference, JSON persistence.
- `index.html`: dependency-free responsive interface.
- `POST.md`: draft submission post.
- `data/memories.json`: private local records (created on first save; not part of source distribution).
