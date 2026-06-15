# LLM Gateway with LiteLLM and LangChain

A practical implementation of an LLM gateway pattern — a unified middleware layer that sits between your application and multiple LLM providers (OpenAI, Anthropic, Groq, Gemini).

## What's covered

- **Unified API** — a single `completion()` call across providers, switching models with just a string change
- **Automatic fallbacks** — transparent failover to alternate providers when one fails
- **Cost tracking** — per-call cost calculation using LiteLLM's built-in pricing data
- **Caching** — avoid redundant calls for repeated queries
- **Smart routing** — least-busy, latency-based, and cost-based routing strategies, plus load balancing across multiple deployments
- **Observability** — custom callbacks for logging prompts, responses, latency, and cost per user
- **LangChain integration** — `ChatLiteLLM` wrapper and LCEL chains with fallback support
- **Task-aware chatbot** — a small end-to-end example that classifies queries and routes them to the appropriate model chain
- **Guardrails** — PII redaction, prompt injection detection, and forbidden topic filtering using LiteLLM callback hooks

## Requirements

- Python 3.10+
- `litellm`, `langchain`, `langchain-community`, `langchain-openai`, `langchain-litellm`, `python-dotenv`

Install with:

```bash
pip install litellm langchain langchain-community langchain-openai langchain-litellm python-dotenv
```

## Setup

Create a `.env` file in the project root with your API keys:

```
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...
GROQ_API_KEY=gsk_...
```

## Usage

Open `llm_gateway_notes.ipynb` and run the cells in order. Each section builds on the previous one, progressing from a basic unified API call to a full gateway with routing, fallbacks, caching, observability, and guardrails.

## Production notes

The notebook closes with a section on production considerations (distributed caching, rate limiting, virtual keys, health checks, configuration management) and a comparison of popular LLM gateway tools (LiteLLM, Portkey, Helicone, Cloudflare AI Gateway, Kong AI Gateway, OpenRouter).

---

*Mehdi Bouhamidi*
