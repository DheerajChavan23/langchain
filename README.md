<div align="center">

# 🔮 LangChain Agents & Tools

A modular LangChain framework for building AI agents and tool-enabled workflows with Gemini, Groq, and OpenAI.

</div>

---

## Overview

A clean, modular LangChain setup for:

- Custom tools (Python functions exposed to LLM agents)
- LLM-powered agents via `create_agent`
- Multiple model providers — Gemini, Groq, OpenAI
- Fast local development with `uv`

## Project Structure

```
langchainupdated/
├── src/
│   ├── agents/       # Agent definitions
│   ├── tools/        # Custom tools exposed to LLMs
│   ├── utils/        # Helper functions
│   └── main.py       # Entry point
├── updatedlangchain/ # Experiments & drafts
├── .env               # API keys (gitignored)
├── pyproject.toml
├── requirement.txt
└── uv.lock
```

## Installation

```bash
git clone https://github.com/DheerajChavan23/langchain.git
cd langchain

uv venv
source .venv/bin/activate   # macOS/Linux
.venv\Scripts\activate      # Windows

uv pip install -r requirement.txt
```

## Environment Variables

Create a `.env` file in the project root:

```
GROQ_API_KEY="your_key"
OPENAI_API_KEY="your_key"
GOOGLE_API_KEY="your_key"
```

⚠️ Never commit `.env` — it's already in `.gitignore`.

## Running

```bash
python src/main.py                    # main agent
python updatedlangchain/<file>.py     # any experiment
```

## Example: Creating an Agent

```python
from langchain.agents import create_agent
from google import genai
import os

client = genai.Client(api_key=os.getenv("GOOGLE_API_KEY"))

def get_weather(city: str) -> str:
    return f"The weather in {city} is sunny."

agent = create_agent(
    model="gemma-2-9b-it",
    tools=[get_weather],
    system_prompt="You are a helpful AI assistant",
)

print(agent("What's the weather in Dublin?"))
```

## Dependencies

`langchain` · `google-genai` · `groq` · `openai` · `python-dotenv` · `uv` · `pytest` (optional)

## Roadmap

- [ ] More tools (search, file ops, API calls)
- [ ] Memory-enabled agents
- [ ] FastAPI wrapper for agent endpoints
- [ ] Vector store (FAISS / Chroma) + RAG pipeline
- [ ] CLI interface
- [ ] Dockerfile for deployment

## Contributing

PRs welcome — open an issue for bugs, features, or docs improvements.

## License

MIT License — free to use, modify, and distribute.

<div align="center">

</div>