# Memori Project Overview

## Project Purpose
**Memori** is **"The memory fabric for enterprise AI"** - a Python SDK that provides persistent memory for LLM applications. It plugs into existing software and infrastructure, is LLM and datastore agnostic, and seamlessly integrates into existing architectures.

## Core Problem Memori Solves
LLM applications lack persistent memory across sessions. Memori enables:
- **Persistent memory** across LLM interactions
- **Context awareness** - remembers user preferences, facts, relationships
- **Multi-session continuity** - maintains context between conversations
- **Enterprise-ready** - works with any LLM, any database, any framework

## Key Features

### 1. **LLM Agnostic**
Supports all major LLM providers:
- OpenAI (sync/async, streaming)
- Anthropic Claude (sync/async, streaming)
- Google Gemini (sync/async, streaming)
- AWS Bedrock
- Grok (xAI)

### 2. **Datastore Agnostic**
Works with any database:
- PostgreSQL, MySQL, MariaDB, SQLite
- MongoDB, CockroachDB
- Oracle, Neon, Supabase
- Django ORM, SQLAlchemy
- Any DB-API 2.0 compatible driver

### 3. **Framework Integration**
- Agno
- LangChain
- Nebius AI Studio

### 4. **Advanced Augmentation**
Enhances memories with:
- Attributes, events, facts
- People, preferences, relationships
- Rules, skills
- Semantic triples for knowledge graphs
- Vectorized memories for semantic search

### 5. **Zero Latency**
Threaded, asynchronous augmentation runs in background with no impact on response time.

### 6. **Third Normal Form Schema**
Structured storage with automatic schema migrations.

## Project Type
- **Python SDK**: Published to PyPI as `memori`
- **Open Source**: Apache 2.0 license
- **Enterprise Ready**: Production-grade reliability
- **Version**: 3.1.2 (current)

## Target Use Cases
- **Enterprise AI Agents**: Persistent memory for customer-facing agents
- **Multi-Agent Systems**: Shared memory across agents
- **Conversational AI**: Context-aware chatbots
- **Knowledge Management**: Semantic knowledge graphs
- **Personalization**: User preference and history tracking

## Quick Start Example
```python
from openai import OpenAI
from memori import Memori

client = OpenAI(...)
mem = Memori(conn=db_session_factory).llm.register(client)
mem.attribution(entity_id="12345", process_id="my-ai-bot")
```

## Attribution Model
Memori requires attribution to create memories:
- **entity_id**: Person, place, or thing (e.g., user ID)
- **process_id**: Agent, LLM interaction, or program

## Session Management
- Automatic session handling by default
- Manual session control: `mem.new_session()` or `mem.set_session(session_id)`
- Sessions group related LLM interactions together

## Advanced Augmentation
- Free tier available (rate limited by IP)
- Sign up for increased limits: `python -m memori sign-up <email>`
- Always free for developers
- Set `MEMORI_API_KEY` environment variable after signup

## Community & Support
- **Documentation**: https://memorilabs.ai/docs
- **Discord**: https://discord.gg/abD4eGym6v
- **GitHub**: https://github.com/MemoriLabs/Memori
- **Website**: https://memorilabs.ai
