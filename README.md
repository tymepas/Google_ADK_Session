# Google ADK Session

A starter AI agent built with [Google Agent Development Kit (ADK)](https://google.github.io/adk-docs/) for the TechConfluence event session.

## Project Structure

```
Google_ADK_Session/
├── agent.py        # Agent definition (root_agent)
├── __init__.py     # Marks folder as a Python package
├── data/           # Input / sample data for the agent
├── eval/           # Evaluation sets and test cases
├── scripts/        # Helper scripts
└── .gitignore
```

## Agent

Defined in `agent.py`:

| Field       | Value                                          |
|-------------|------------------------------------------------|
| Name        | `root_agent`                                   |
| Model       | `gemini-3.5-flash`                             |
| Description | A helpful assistant for user questions         |
| Instruction | Answer user questions to the best of knowledge |

## Prerequisites

- Python 3.10+
- A Gemini API key from [Google AI Studio](https://aistudio.google.com/apikey)

## Setup

```powershell
# 1. Create and activate virtual environment (Windows PowerShell)
python -m venv .venv
.\.venv\Scripts\Activate.ps1

# 2. Install ADK
pip install google-adk
```

macOS / Linux:

```bash
python -m venv .venv
source .venv/bin/activate
pip install google-adk
```

## Configuration

ADK expects the agent folder to sit inside a parent folder. Place this repo as a subfolder, for example:

```
parent_folder/
└── Google_ADK_Session/   <- this repo
```

Create a `.env` file inside this repo folder:

```
GOOGLE_API_KEY=your_api_key_here
```

`.env` is git-ignored. Never commit API keys.

## Run

Run from the **parent folder** that contains this repo:

```bash
# Web UI
adk web

# Terminal chat
adk run Google_ADK_Session
```

Open the URL printed in the terminal (default `http://localhost:8000`) and pick the agent from the dropdown.

## Customize

Edit `agent.py` to change the model, instruction, or add tools:

```python
from google.adk.agents.llm_agent import Agent

root_agent = Agent(
    model='gemini-3.5-flash',
    name='root_agent',
    description='A helpful assistant for user questions.',
    instruction='Answer user questions to the best of your knowledge',
)
```

## Notes

- `__pycache__/`, `*.pyc`, `.env`, `.venv/` are excluded via `.gitignore`.
- Telemetry prompt during setup is optional and does not affect the agent.

## Resources

- [ADK Documentation](https://google.github.io/adk-docs/)
- [Google AI Studio](https://aistudio.google.com/)
