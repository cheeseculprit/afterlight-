# Afterlight — an archive of ordinary things

For Ghost in the Machine, I built a small, private space for remembering someone through an object they left in your life: a chipped cup, a recipe card, a key. You write what you actually remember. Afterlight uses Qwen3 1.7B running locally through Ollama to draft a museum-style label, a single reflective line, and a question that might bring another detail to mind. Your original words stay visible beside the draft, and you can edit or delete the AI's wording. It does not pretend to speak as the person who is gone.

Open AI is the reason this project can exist in its current form. The model runs on my laptop rather than requiring a hosted inference account. Once Ollama and the model are downloaded, the interface, generation, and JSON archive can run without internet; no private memory needs to be sent to a server I don't control. The app itself uses only Python's standard library and a dependency-free HTML page. I can change the prompt, replace the model with another compatible Ollama model, and inspect the entire path from input to saved record.

The advantage over a closed cloud API here isn't a measured writing-quality win. It's control: local inference, no per-request API bill, and the ability to keep intimate source material on this machine. My first real test also exposed a limitation: the small model embellished a memory with an imagined detail. I tightened the prompt and added editing, but I don't treat generated prose as evidence. The human memory is the source; the model is a fallible writing aid.

Built with: Ollama, Qwen3 1.7B, Python, HTML/CSS/JavaScript. Run locally at `http://127.0.0.1:8765` after `ollama pull qwen3:1.7b` and `python server.py`. Source and setup instructions are in the project folder.
