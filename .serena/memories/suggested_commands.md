# Memori Suggested Commands

## Development Setup

### Initial Setup
```bash
# Install uv (if not already installed)
curl -LsSf https://astral.sh/uv/install.sh | sh

# Clone repository (if needed)
git clone https://github.com/MemoriLabs/Memori.git
cd Memori

# Install dependencies
uv sync

# Install pre-commit hooks
uv run pre-commit install

# Copy environment file
cp .env.example .env
# Edit .env and add API keys (optional for unit tests, required for integration tests)
```

### Docker Setup (Alternative)
```bash
# Start development environment
make dev-up

# Enter development container
make dev-shell

# Stop environment
make dev-down

# Clean everything (containers, volumes, cache)
make dev-clean
```

## Code Quality Commands

### Formatting
```bash
# Format code (local)
uv run ruff format .

# Format code (Docker)
make format
```

### Linting
```bash
# Check linting (local)
uv run ruff check .

# Check linting (Docker)
make lint

# Auto-fix linting issues
uv run ruff check --fix .
```

### Type Checking
```bash
# Run type checker
uvx ty check
```

### Security Scans
```bash
# Run security scans (local)
uv run bandit -r memori -ll -ii
uv run pip-audit --require-hashes --disable-pip || true

# Run security scans (Docker)
make security
```

### Pre-commit Hooks
```bash
# Install hooks (one-time)
uv run pre-commit install

# Run manually
uv run pre-commit run --all-files

# Run on all files
uv run pre-commit run --all-files
```

## Testing Commands

### Unit Tests (Local)
```bash
# Run all tests
uv run pytest

# Run with coverage
uv run pytest --cov=memori

# Run specific test file
uv run pytest tests/memory/test_memory.py

# Run specific test
uv run pytest tests/memory/test_memory.py::test_specific_function

# Run async tests only
uv run pytest -m asyncio

# Exclude benchmarks
uv run pytest -m "not benchmark"
```

### Unit Tests (Docker)
```bash
# Run all tests
make test

# Run in container shell
make dev-shell
pytest
```

### Integration Tests
```bash
# Initialize database schemas
make init-postgres   # PostgreSQL
make init-mysql      # MySQL
make init-mongodb    # MongoDB
make init-sqlite     # SQLite
make init-oracle     # Oracle

# Run specific integration test
make run-integration FILE=tests/llm/clients/oss/openai/async.py

# Run with arguments
make run-integration FILE=tests/llm/clients/oss/openai/sync.py ARGS="--db mysql"

# Run in enterprise mode
make run-integration-enterprise FILE=tests/llm/clients/oss/openai/sync.py
```

## Database Commands

### Initialize Schemas
```bash
# PostgreSQL
make init-postgres
# or: docker compose exec -e PYTHONPATH=/app dev python tests/build/postgresql.py

# MySQL
make init-mysql
# or: docker compose exec -e PYTHONPATH=/app dev python tests/build/mysql.py

# MongoDB
make init-mongodb
# or: docker compose exec -e PYTHONPATH=/app dev python tests/build/mongodb.py

# SQLite
make init-sqlite
# or: docker compose exec -e PYTHONPATH=/app dev python tests/build/sqlite.py

# Oracle
make init-oracle
# or: docker compose exec -e PYTHONPATH=/app dev python tests/build/oracle.py

# Initialize all databases for integration tests
make init-db
```

## Docker Commands

### Development Environment
```bash
# Start environment (builds and runs containers)
make dev-up

# Stop environment
make dev-down

# Open shell in container
make dev-shell

# Rebuild container
make dev-build

# Complete teardown (containers, images, cache)
make dev-clean
```

### Direct Docker Commands
```bash
# Start containers
docker compose up -d --build

# Stop containers
docker compose down

# View logs
docker compose logs -f

# Execute command in container
docker compose exec dev <command>

# Remove volumes
docker compose down -v
```

## Memori CLI Commands

### Setup
```bash
# Setup environment (one-time, optional)
python -m memori setup
```

### Account Management
```bash
# Sign up for Advanced Augmentation
python -m memori sign-up <email_address>

# Check quota
python -m memori quota
```

## Git Commands (Windows)

### Basic Operations
```bash
# Status
git status

# Add files
git add .

# Commit
git commit -m "Your message"

# Push
git push

# Pull
git pull
```

### Branching
```bash
# Create branch
git checkout -b feature/your-feature

# Switch branch
git checkout main

# List branches
git branch
```

## File System Commands (Windows)

### Navigation
```bash
# Change directory
cd <path>

# List files
dir
# or: ls (if using PowerShell/Git Bash)

# Current directory
cd
```

### File Operations
```bash
# Find files
dir /s <filename>
# or: Get-ChildItem -Recurse -Filter <filename> (PowerShell)

# Find text in files
findstr /s /i "pattern" *
# or: Select-String -Pattern "pattern" -Recurse (PowerShell)
```

## Coverage Reports

### View Coverage
```bash
# Terminal output (automatic with pytest --cov)
uv run pytest --cov=memori

# HTML report
# After running tests, open: htmlcov/index.html
# Windows: start htmlcov/index.html
# or: explorer htmlcov/index.html

# XML report
# Generated at: coverage.xml
```

## Build & Distribution

### Build Package
```bash
# Build wheel
python -m build

# Check build
python -m twine check dist/*
```

### Install Locally
```bash
# Install in development mode
uv pip install -e .

# Install from source
uv pip install .
```

## Utility Commands

### Python Environment
```bash
# Activate virtual environment (if using venv)
# Windows: .venv\Scripts\activate
# PowerShell: .venv\Scripts\Activate.ps1

# Check Python version
python --version

# Check installed packages
uv pip list
```

### Project Information
```bash
# Show help
make help

# Check project version
python -c "import memori; print(memori.__version__)"
```
