# Memori Code Style & Conventions

## General Principles
- **KISS (Keep It Simple, Stupid)**: Lean, simple code preferred
- **YAGNI (You Aren't Gonna Need It)**: Minimize unnecessary complexity
- **Self-documenting code**: Minimize comments - code should explain itself
- **Type safety**: Full type hints for all public APIs

## Python Version & Compatibility
- **Target**: Python 3.12 (for development)
- **Minimum**: Python 3.10
- **Features**: Use modern Python 3.10+ syntax

## Code Formatting (Ruff)

### Configuration
- **Line length**: 88 characters (Black-compatible)
- **Target version**: Python 3.10
- **Quote style**: Double quotes
- **Indent style**: Spaces

### Lint Rules (pyproject.toml)
```toml
select = [
    "E",   # pycodestyle errors
    "W",   # pycodestyle warnings
    "F",   # pyflakes
    "I",   # isort
    "B",   # flake8-bugbear
    "C4",  # flake8-comprehensions
    "UP",  # pyupgrade
]
ignore = [
    "E501",  # line too long (handled by formatter)
]
```

### Per-file Ignores
- `memori/storage/__init__.py`: Import order matters for adapter registration (`I001`)

## Type Checking

### Tool
- **ty**: Type checker (via `uvx ty check`)
- **Python version**: 3.12 (for type checking)
- **Exclusions**: 
  - `tests/llm/clients/**/*.py`
  - `**/__pycache__/**`

### Type Hints Requirements
- **All public APIs**: Must have type hints
- **PEP 561**: Marked with `py.typed` file
- **Modern syntax**: Use `|` for unions (Python 3.10+), not `Union`

## Naming Conventions

### Variables & Functions
- **snake_case**: For variables and functions
- **Descriptive**: Clear, meaningful names
- **No abbreviations**: Unless widely understood

### Classes
- **PascalCase**: For class names
- **Noun-based**: Represent entities or concepts

### Constants
- **UPPER_SNAKE_CASE**: For module-level constants

### Private Members
- **Single underscore prefix**: For internal use
- **Double underscore**: For name mangling (rare)

## Comments & Docstrings

### Comments
- **Minimal**: Code should be self-documenting
- **When needed**: Explain "why", not "what"
- **Complex logic**: Brief explanation for non-obvious code

### Docstrings
- **Public APIs**: Required
- **Style**: Google or NumPy style (consistent throughout)
- **Type info**: Include parameter types and return types

## Error Handling

### Exception Types
- **Specific exceptions**: Catch specific types
- **Never bare except**: Always specify exception type
- **Custom exceptions**: In `memori/_exceptions.py`

## Project Structure

### Module Organization
```
memori/
  __init__.py          # Main Memori class, public API
  _cli.py              # CLI commands
  _config.py           # Configuration
  _exceptions.py       # Custom exceptions
  _network.py          # Network utilities
  _search.py           # Search functionality
  _setup.py            # Setup utilities
  _utils.py            # General utilities
  llm/                 # LLM provider integrations
    adapters/          # LLM adapter implementations
  memory/              # Memory system
  storage/             # Storage adapters
    adapters/          # Storage adapter implementations
    drivers/           # Database drivers
    migrations/       # Schema migrations
  api/                 # API client
```

### File Naming
- **snake_case.py**: Module names
- **test_*.py**: Test files
- **_*.py**: Private/internal modules

## Testing Standards

### Test Organization
```
tests/
  build/              # Database initialization scripts
  llm/                # LLM provider tests
  memory/             # Memory system tests
  storage/            # Storage adapter tests
  benchmarks/         # Performance benchmarks
```

### Test Naming
- **test_*.py**: Test files
- **test_*()**: Test functions
- **Test***: Test classes

### Test Markers
- **@pytest.mark.asyncio**: Async tests
- **@pytest.mark.benchmark**: Performance benchmarks

### Coverage
- **High coverage**: Maintained automatically
- **Reports**: Terminal, HTML (`htmlcov/`), XML (`coverage.xml`)

## Import Organization

### Order
1. Standard library imports
2. Third-party imports
3. Local application imports

### Style
- **Alphabetically sorted**: Within each group (via isort/ruff)
- **One import per line**: For clarity

## Git Conventions

### Pre-commit Hooks
- **Automatic**: Format and lint on commit
- **Install**: `uv run pre-commit install`
- **Manual run**: `uv run pre-commit run --all-files`

### Commit Messages
- **Clear and descriptive**: What and why
- **Present tense**: "Add feature" not "Added feature"

## Code Review Standards

### Before Submitting PR
- [ ] All tests pass
- [ ] Type checking passes (`uvx ty check`)
- [ ] Linting passes (`uv run ruff check .`)
- [ ] Formatting passes (`uv run ruff format .`)
- [ ] Security scans pass (`bandit`, `pip-audit`)
- [ ] Code coverage maintained/improved
- [ ] Documentation updated (if needed)
- [ ] CHANGELOG.md updated (if applicable)
