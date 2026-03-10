# Contributing to fluxopt-yaml

Contributions are welcome — bug reports, code, docs, examples.

## Setup

```bash
git clone https://github.com/FBumann/fluxopt-yaml.git
cd fluxopt-yaml
uv sync --group dev
uv run pre-commit install
uv run pytest -v
```

## Workflow

1. Create a branch from `main`
2. Make changes, commit with clear messages
3. Push and open a PR
4. Ensure CI passes

## Code Quality

Ruff runs automatically via pre-commit. Manual checks:

```bash
uv run ruff check --fix .
uv run ruff format .
uv run pytest -v
```

## Testing

Tests live in `tests/`. Write tests for new functionality.

```bash
uv run pytest                           # Full suite
uv run pytest tests/test_loader.py      # Single file
uv run pytest -k "keyword"             # By keyword
```
