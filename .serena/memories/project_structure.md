# Memori Project Structure

## Root Directory Layout

```
Memori/
├── .github/              # GitHub Actions workflows
├── .serena/              # Serena MCP metadata (auto-generated)
├── docs/                 # Documentation
├── examples/             # Example implementations
│   ├── agno/             # Agno framework example
│   ├── cockroachdb/      # CockroachDB example
│   ├── digitalocean/     # DigitalOcean example
│   ├── mongodb/          # MongoDB example
│   ├── nebius/           # Nebius AI Studio example
│   ├── neon/             # Neon example
│   ├── postgres/         # PostgreSQL example
│   └── sqlite/           # SQLite example
├── memori/               # Main SDK source code
│   ├── api/              # Memori Advanced Augmentation API client
│   ├── llm/              # LLM provider integrations
│   │   └── adapters/     # LLM adapter implementations
│   ├── memory/           # Memory system and augmentation
│   ├── storage/          # Storage adapters
│   │   ├── adapters/     # Storage adapter implementations
│   │   ├── cockroachdb/  # CockroachDB specific code
│   │   ├── drivers/      # Database drivers
│   │   └── migrations/   # Schema migrations
│   ├── _cli.py           # CLI commands
│   ├── _config.py        # Configuration
│   ├── _exceptions.py    # Custom exceptions
│   ├── _network.py       # Network utilities
│   ├── _search.py         # Search functionality
│   ├── _setup.py         # Setup utilities
│   ├── _utils.py         # General utilities
│   ├── __init__.py       # Main Memori class, public API
│   ├── __main__.py       # CLI entry point
│   └── py.typed          # PEP 561 type marker
├── tests/                # Test suite
│   ├── benchmarks/       # Performance benchmarks
│   ├── build/            # Database initialization scripts
│   ├── llm/              # LLM provider tests
│   ├── memory/           # Memory system tests
│   └── storage/          # Storage adapter tests
├── .dockerignore         # Docker ignore patterns
├── .env.example          # Environment variables template
├── .gitignore           # Git ignore patterns
├── .pre-commit-config.yaml # Pre-commit hooks configuration
├── CHANGELOG.md          # Version history
├── conftest.py           # Pytest configuration
├── CONTRIBUTING.md       # Contribution guidelines
├── docker-compose.yml    # Docker Compose configuration
├── Dockerfile            # Docker image definition
├── LICENSE               # Apache 2.0 license
├── Makefile              # Development commands
├── MANIFEST.in           # Package data inclusion
├── pyproject.toml        # Project metadata and dependencies
├── README.md             # Project overview
└── SECURITY.md           # Security policy
```

## Source Code Structure (`memori/`)

### Main Package (`memori/`)
- **`__init__.py`**: Main `Memori` class, `LlmRegistry`, public API exports
- **`__main__.py`**: CLI entry point (`python -m memori`)
- **`py.typed`**: PEP 561 type marker for type checking
- **`_cli.py`**: Command-line interface implementation
- **`_config.py`**: Configuration management
- **`_exceptions.py`**: Custom exception classes
- **`_network.py`**: Network/HTTP utilities
- **`_search.py`**: Semantic search functionality
- **`_setup.py`**: Environment setup utilities
- **`_utils.py`**: General utility functions

### LLM Module (`memori/llm/`)
- **`__init__.py`**: LLM registry and provider exports
- **`_base.py`**: Base classes for LLM integration
- **`_clients.py`**: LLM client implementations
- **`_constants.py`**: LLM-related constants
- **`_embeddings.py`**: Embedding generation
- **`_invoke.py`**: LLM invocation logic
- **`_iterable.py`**: Iterable response handling
- **`_iterator.py`**: Iterator implementations
- **`_providers.py`**: LLM provider definitions
- **`_registry.py`**: LLM registry implementation
- **`_streaming.py`**: Streaming response handling
- **`_utils.py`**: LLM utility functions
- **`_xai_wrappers.py`**: xAI (Grok) specific wrappers
- **`adapters/`**: LLM adapter implementations (OpenAI, Anthropic, Google, etc.)

### Memory Module (`memori/memory/`)
- Memory system and Advanced Augmentation integration
- Handles memory creation, retrieval, and enhancement
- Semantic search and knowledge graph functionality

### Storage Module (`memori/storage/`)
- **`__init__.py`**: Storage registry and adapter exports
- **`_base.py`**: Base storage adapter classes
- **`_builder.py`**: Schema builder
- **`_connection.py`**: Connection management
- **`_manager.py`**: Storage manager
- **`_registry.py`**: Storage adapter registry
- **`adapters/`**: Storage adapter implementations (PostgreSQL, MySQL, MongoDB, etc.)
- **`cockroachdb/`**: CockroachDB-specific code
- **`drivers/`**: Database driver abstractions
- **`migrations/`**: Automatic schema migrations

### API Module (`memori/api/`)
- Client for Memori Advanced Augmentation API
- Handles API authentication and requests
- Manages quota and rate limiting

## Test Structure (`tests/`)

### Test Organization
- **`conftest.py`**: Shared pytest fixtures
- **`build/`**: Database initialization scripts
  - `postgresql.py`, `mysql.py`, `mongodb.py`, `sqlite.py`, `oracle.py`
- **`llm/`**: LLM provider tests
  - Unit tests with mocks
  - Integration tests with real LLM providers
- **`memory/`**: Memory system tests
- **`storage/`**: Storage adapter tests
- **`benchmarks/`**: Performance benchmarks (excluded from regular test runs)

### Test Patterns
- **Unit tests**: Use mocks, no external dependencies
- **Integration tests**: Require database and LLM API keys
- **Test markers**: `@pytest.mark.asyncio`, `@pytest.mark.benchmark`

## Examples Structure (`examples/`)

Each example directory contains:
- **`README.md`**: Setup instructions and usage
- **`pyproject.toml`**: Example-specific dependencies
- **`main.py`** or similar: Working example code

## Configuration Files

### Python Configuration
- **`pyproject.toml`**: Project metadata, dependencies, tool settings
  - Ruff configuration (linting, formatting)
  - Pytest configuration
  - Coverage configuration
  - Type checking configuration

### Docker Configuration
- **`Dockerfile`**: Development container definition
- **`docker-compose.yml`**: Multi-container setup (PostgreSQL, MySQL, MongoDB)
- **`.dockerignore`**: Files excluded from Docker builds

### Git Configuration
- **`.gitignore`**: Files excluded from version control
- **`.pre-commit-config.yaml`**: Pre-commit hooks (ruff, ty, pytest)

### Development Configuration
- **`.env.example`**: Environment variables template
- **`Makefile`**: Development commands
- **`MANIFEST.in`**: Package data inclusion for PyPI

## Key Files by Purpose

### User-Facing Documentation
- **README.md**: Project overview, quick start, features
- **CONTRIBUTING.md**: Development setup and guidelines
- **CHANGELOG.md**: Version history
- **SECURITY.md**: Security policy

### Entry Points
- **`memori/__init__.py`**: Main SDK interface (`from memori import Memori`)
- **`memori/__main__.py`**: CLI entry point (`python -m memori`)

### Core Implementation
- **`memori/llm/`**: LLM provider integrations
- **`memori/memory/`**: Memory system
- **`memori/storage/`**: Storage adapters
- **`memori/api/`**: Advanced Augmentation API client

## Import Patterns

### Public API (Users)
```python
from memori import Memori

mem = Memori(conn=db_session_factory).llm.register(client)
```

### Internal Modules (Developers)
```python
from memori.llm._registry import LlmRegistry
from memori.storage._adapter import StorageAdapter
from memori.memory._system import MemorySystem
```

## Build Artifacts (Gitignored)

### Python Cache
- **`__pycache__/`**: Bytecode cache
- **`*.pyc`**: Compiled Python files
- **`.pytest_cache/`**: pytest cache
- **`.ruff_cache/`**: ruff cache

### Development
- **`.venv/`**: Virtual environment
- **`venv/`**: Alternative venv name
- **`.env`**: Environment variables (secrets)

### Build Output
- **`dist/`**: Build distributions
- **`build/`**: Build artifacts
- **`*.egg-info/`**: Package metadata

### Coverage Reports
- **`htmlcov/`**: Coverage HTML reports
- **`coverage.xml`**: Coverage XML report
- **`.coverage`**: Coverage data file

## Navigation Guidelines

### Finding Core Logic
1. Start at **`memori/__init__.py`** for public API
2. Look in **`memori/llm/`** for LLM integrations
3. Check **`memori/memory/`** for memory system
4. See **`memori/storage/`** for database adapters

### Finding Tests
1. **`tests/llm/`** for LLM tests
2. **`tests/memory/`** for memory tests
3. **`tests/storage/`** for storage tests
4. Match test file to source: `memori/llm/_registry.py` → `tests/llm/test_registry.py`

### Finding Examples
1. **`examples/`** for working examples
2. Each example has its own `README.md` with setup instructions
