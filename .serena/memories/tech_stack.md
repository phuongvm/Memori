# Memori Technology Stack

## Programming Language
- **Python**: 3.10+ (3.12 recommended for development)
- **Type Hints**: Full type annotation support (PEP 561 via `py.typed`)

## Package Management
- **uv**: Fast Python package installer (primary tool)
- **setuptools**: Build backend for PyPI distribution

## Core Dependencies

### Runtime Dependencies
- **aiohttp** (>=3.9.0): Async HTTP client
- **botocore** (>=1.34.0): AWS SDK for Bedrock
- **faiss-cpu** (>=1.7.0): Vector similarity search
- **grpcio** (>=1.60.0): gRPC for API communication
- **numpy** (>=1.24.0): Numerical computing
- **protobuf** (>=4.25.0,<6.0.0): Protocol buffers
- **psycopg[binary]** (>=3.1.0): PostgreSQL driver
- **pyfiglet** (>=0.8.0): ASCII art for CLI
- **requests** (>=2.32.5): HTTP library
- **sentence-transformers** (>=3.0.0): Embeddings for semantic search

### Development Dependencies (dependency-groups)
- **agno** (>=2.0.0): Framework integration
- **anthropic** (>=0.71.0): Anthropic Claude client
- **bandit** (>=1.8.0): Security linting
- **google-genai** (>=1.46.0): Google Gemini client
- **langchain-community** (>=0.3.0): LangChain integration
- **langchain-core** (>=1.0.1): LangChain core
- **langchain-google-genai** (>=3.0.0): LangChain Google integration
- **langchain-google-vertexai** (>=2.0.0): LangChain Vertex AI
- **langchain-openai** (>=1.0.1): LangChain OpenAI
- **openai** (>=2.6.0): OpenAI client
- **oracledb** (>=3.0.0): Oracle database driver
- **pip-audit** (>=2.8.0): Dependency vulnerability scanning
- **pre-commit** (>=4.0.0): Git hooks
- **psycopg2-binary** (>=2.9.0): PostgreSQL driver (legacy)
- **pymongo** (>=4.15.3): MongoDB driver
- **pymysql** (>=1.1.2): MySQL driver
- **pytest** (>=8.4.2): Testing framework
- **pytest-asyncio** (>=0.24.0): Async test support
- **pytest-benchmark** (>=4.0.0): Performance benchmarks
- **pytest-cov** (>=6.0.0): Coverage reporting
- **pytest-mock** (>=3.15.1): Mocking utilities
- **psutil** (>=5.9.0): System utilities
- **ruff** (>=0.8.0): Linting and formatting
- **sqlalchemy** (>=2.0.44): SQL toolkit and ORM
- **sqlalchemy-cockroachdb** (>=1.4.0): CockroachDB adapter
- **xai-sdk** (>=1.3.1): xAI Grok client

## Development Tools

### Code Quality
- **Ruff**: Linting and formatting (replaces Black, isort, flake8)
- **ty**: Type checking (via `uvx ty check`)
- **Bandit**: Security linting
- **pip-audit**: Dependency vulnerability scanning

### Testing
- **pytest**: Test framework
- **pytest-asyncio**: Async test support
- **pytest-cov**: Coverage reporting
- **pytest-mock**: Mocking
- **pytest-benchmark**: Performance testing

### Pre-commit Hooks
- **pre-commit**: Git hooks automation
- **ruff-check**: Linting on commit
- **ruff-format**: Formatting on commit
- **ty**: Type checking on commit
- **pytest**: Run tests on commit

## Infrastructure

### Docker
- **Docker Compose**: Development environment
- **PostgreSQL**: Integration testing
- **MySQL**: Integration testing
- **MongoDB**: Integration testing
- **Mongo Express**: MongoDB web UI (port 8081)

### Database Drivers Supported
- **PostgreSQL**: psycopg2, psycopg3
- **MySQL/MariaDB**: pymysql
- **MongoDB**: pymongo
- **Oracle**: cx_Oracle, python-oracledb
- **SQLite**: stdlib
- **CockroachDB**: sqlalchemy-cockroachdb
- **Django ORM**: Native integration
- **SQLAlchemy**: Native integration
- **DB-API 2.0**: Any PEP 249 compatible driver

## Build System
- **setuptools**: Build backend
- **wheel**: Distribution format
- **MANIFEST.in**: Package data inclusion

## Platform Support
- **Cross-platform**: Windows, Linux, macOS
- **Windows-specific**: This instance runs on Windows
- **Async-first**: Built on asyncio

## External Services
- **Memori Advanced Augmentation API**: Cloud service for memory enhancement
- **LLM Providers**: OpenAI, Anthropic, Google, AWS, xAI
- **Vector Search**: FAISS for in-memory semantic search
