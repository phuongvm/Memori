# Memori Task Completion Checklist

## Before Marking Task Complete

### Code Quality
- [ ] **Formatting**: Code is formatted (`uv run ruff format .` or `make format`)
- [ ] **Linting**: No linting errors (`uv run ruff check .` or `make lint`)
- [ ] **Type Checking**: Type checks pass (`uvx ty check`)
- [ ] **Security**: Security scans pass (`make security` or manual `bandit` + `pip-audit`)

### Testing
- [ ] **Unit Tests**: All unit tests pass (`uv run pytest` or `make test`)
- [ ] **Test Coverage**: Coverage maintained or improved
- [ ] **New Tests**: Added tests for new functionality
- [ ] **Integration Tests**: Integration tests pass (if applicable)
  - [ ] Database schemas initialized (`make init-postgres`, etc.)
  - [ ] API keys configured in `.env`
  - [ ] Integration tests run successfully

### Documentation
- [ ] **Code Comments**: Code is self-documenting (minimal comments needed)
- [ ] **Type Hints**: All public APIs have type hints
- [ ] **Docstrings**: Public functions/classes have docstrings
- [ ] **README**: Updated if adding new features (if applicable)
- [ ] **CHANGELOG**: Added entry under "Unreleased" (if applicable)

### Git & Version Control
- [ ] **Pre-commit Hooks**: All hooks pass (`uv run pre-commit run --all-files`)
- [ ] **Commit Message**: Clear, descriptive commit message
- [ ] **Atomic Commits**: Commits are focused and well-described
- [ ] **Branch**: Working on feature branch (not main)

### Pull Request (if applicable)
- [ ] **Fork & Branch**: Created feature branch from `main`
- [ ] **Tests Pass**: All CI checks pass
- [ ] **Code Review**: Addressed review comments
- [ ] **Documentation**: Updated docs if needed
- [ ] **Breaking Changes**: Documented if any

## Quick Verification Commands

### Run All Checks
```bash
# Local development
uv run pre-commit run --all-files
uv run pytest

# Docker development
make lint
make test
make security
```

### Check Coverage
```bash
uv run pytest --cov=memori --cov-report=term-missing
# Review coverage report, ensure no significant drops
```

### Final Checklist
```bash
# 1. Format
uv run ruff format .

# 2. Lint
uv run ruff check .

# 3. Type check
uvx ty check

# 4. Test
uv run pytest

# 5. Security
uv run bandit -r memori -ll -ii
uv run pip-audit --require-hashes --disable-pip || true

# 6. Pre-commit (runs all above)
uv run pre-commit run --all-files
```

## Integration Test Checklist (if applicable)

- [ ] **Database Setup**: Required database schemas initialized
- [ ] **API Keys**: LLM provider API keys set in `.env`
- [ ] **Test Execution**: Integration tests run successfully
- [ ] **Multiple Databases**: Tested on multiple database backends (if applicable)
- [ ] **Multiple LLMs**: Tested with multiple LLM providers (if applicable)

## Documentation Checklist

- [ ] **Public API**: All new public functions/classes documented
- [ ] **Examples**: Added examples if introducing new features
- [ ] **Breaking Changes**: Documented in CHANGELOG.md
- [ ] **Migration Guide**: Added if schema changes (if applicable)

## Release Checklist (for maintainers)

- [ ] **Version Bump**: Updated version in `pyproject.toml`
- [ ] **CHANGELOG**: Moved "Unreleased" entries to version section
- [ ] **Tag**: Created git tag for release
- [ ] **PyPI**: Built and published package
- [ ] **Documentation**: Updated online docs (if applicable)
