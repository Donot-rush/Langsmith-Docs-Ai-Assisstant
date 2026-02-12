**Maintained & Customized by: Manu Jain**


# Chat LangChain

> A simple documentation assistant built with LangGraph.

[![LangGraph](https://img.shields.io/badge/Built%20with-LangGraph-blue)](https://langchain-ai.github.io/langgraph/)
[![Python](https://img.shields.io/badge/Python-3.11+-green)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

### 📸 Demo Screenshots

### Studio Chat
![Studio Chat](screenshots/studio%20chat.png)

### Studio Graph
![Studio Graph](screenshots/Studio%20graph.png)



## Overview

This is a documentation assistant agent that helps answer questions about LangChain, LangGraph, and LangSmith. It demonstrates how to build a production-ready agent using:

## 🔧 My Enhancements

- Customized model configuration for faster responses
- Switched default model to GPT-5 Nano
- Optimized guardrails middleware
- Debugged circular imports and tool failures
- Configured LangGraph local dev deployment
- Added environment-based provider switching


- **LangGraph** - For agent orchestration and state management
- **LangChain Agents** - For agent creation with middleware support
- **Guardrails** - To keep conversations on-topic

## Features

- **Documentation Search** - Searches official LangChain docs
- **Support KB** - Searches the Pylon knowledge base for known issues
- **Link Validation** - Verifies URLs before including in responses
- **Guardrails** - Filters off-topic queries

## Quick Start

### Prerequisites

- Python 3.11+
- [uv](https://github.com/astral-sh/uv) (recommended) or pip

### Installation

```bash
# Clone the repository
git clone 
cd chat-langchain

# Install dependencies with uv
uv sync

# Or with pip
pip install -e . "langgraph-cli[inmem]"
```

### Configuration

```bash
# Copy environment template
cp .env.example .env

# Edit .env with your API keys
```

#### Required Environment Variables

| Variable | Description |
|----------|-------------|
| `ANTHROPIC_API_KEY` | Anthropic API key (or use another provider) |
| `MINTLIFY_API_KEY` | Mintlify API key for docs search |
| `PYLON_API_KEY` | Pylon API key for support KB |

### Running Locally

```bash
# Start LangGraph development server
uv run langgraph dev

# Or with pip
langgraph dev
```

Open LangGraph Studio: <https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024>

## Project Structure

```txt
├── src/
│   ├── agent/
│   │   ├── docs_graph.py      # Main docs agent
│   │   └── config.py          # Model configuration
│   ├── tools/
│   │   ├── docs_tools.py      # Documentation search
│   │   ├── pylon_tools.py     # Support KB tools
│   │   └── link_check_tools.py # URL validation
│   ├── prompts/
│   │   └── docs_agent_prompt.py
│   └── middleware/
│       ├── guardrails_middleware.py
│       └── retry_middleware.py
├── langgraph.json             # LangGraph configuration
└── pyproject.toml             # Python project config
```

## How It Works

The agent uses a docs-first research strategy:

1. **Guardrails Check** - Validates the query is LangChain-related
2. **Documentation Search** - Searches official docs via Mintlify
3. **Knowledge Base** - Searches Pylon for known issues/solutions
4. **Link Validation** - Verifies any URLs before including them
5. **Response Generation** - Synthesizes a helpful answer

## Deployment

### LangGraph Cloud

1. Push to GitHub
2. Connect repository in [LangSmith](https://smith.langchain.com/)
3. Configure environment variables
4. Deploy

## Resources

- [LangChain Documentation](https://docs.langchain.com/oss/python/langchain/overview)
- [LangGraph Documentation](https://docs.langchain.com/oss/python/langgraph/overview)
- [LangSmith Documentation](https://docs.langchain.com/langsmith/home)

## License

MIT

**Based on LangChain’s Chat LangChain example project**
       **Customized and extended by Manu Jain**