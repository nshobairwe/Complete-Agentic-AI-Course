# LangChain Update

A hands-on set of Jupyter notebooks for learning LangChain v1 concepts. The examples use local Ollama models by default and also demonstrate integrations with OpenAI, Google Gemini, and Groq.

## What is included

| Notebook | Topic |
| --- | --- |
| `1-langchainintro.ipynb` | LangChain v1 introduction and a simple tool-using agent |
| `2-modelintegration.ipynb` | OpenAI, Google Gemini, Groq, and Ollama chat-model integrations |
| `3-tools.ipynb` | Defining tools, binding tools to models, and executing tool-call loops |
| `4-messages.ipynb` | System, human, AI, and tool messages |
| `5-structuredoutput.ipynb` | Pydantic schemas and structured model responses |
| `6-middleware.ipynb` | Agent middleware and conversation summarization |

## Prerequisites

- Python 3.11 or newer
- [uv](https://docs.astral.sh/uv/) (recommended) or `pip`
- [Ollama](https://ollama.com/) for the local-model examples
- An API key for any cloud provider whose examples you want to run

Start Ollama and download one of the models used in the notebooks:

```powershell
ollama pull qwen2.5:3b
```

Some middleware examples use `qwen3:4b`; model-integration examples may also use `gpt-oss:120b-cloud`.

## Setup

Create a local environment and install the project dependencies:

```powershell
uv sync
```

The notebooks additionally use Ollama, LangGraph, Pydantic, and Jupyter. Install them if they are not already available in your environment:

```powershell
uv add langchain-ollama langgraph pydantic jupyter
```

Alternatively, using `pip`:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt langchain-ollama langgraph pydantic jupyter
```

## Configuration

Create a `.env` file in the project root. Only configure the providers you intend to use; Ollama runs locally and needs no API key.

```env
OPENAI_API_KEY=your_openai_api_key
GOOGLE_API_KEY=your_google_api_key
GROQ_API_KEY=your_groq_api_key
```

Keep `.env` private. It is ignored by Git and should never be committed.

## Run the notebooks

Launch Jupyter from the project root:

```powershell
uv run jupyter lab
```

Then open the notebooks in `updatedlangchain/` and work through them in numerical order. Run the setup cells first in the provider-integration notebook so environment variables are loaded.

## Project layout

```text
.
+-- updatedlangchain/       # Lesson notebooks
+-- src/langchainupdate/    # Minimal Python package
+-- pyproject.toml          # Project metadata and uv dependencies
+-- requirements.txt        # pip dependency list
`-- .env                    # Local API keys (not committed)
```

## Notes

- Cloud-model notebook cells incur usage under the relevant provider account.
- The tool and hotel-search examples use demonstration functions; they do not retrieve live weather or hotel data.
- Model names and provider availability can change. Replace a model name in a notebook with one available in your own account or Ollama installation when necessary.
