# Contributing to ACE-Step

Thank you for your interest in contributing to ACE-Step! This document provides guidelines and instructions for contributing.

## Development Setup

### Prerequisites

- Python 3.11
- CUDA-capable GPU (recommended) or CPU/MPS
- [uv](https://github.com/astral-sh/uv) package manager (recommended) or pip

### Installation

1. Clone the repository:
```bash
git clone https://github.com/ACE-Step/ACE-Step-1.5.git
cd ACE-Step-1.5
```

2. Install dependencies using uv:
```bash
uv sync --group dev
```

Or using pip:
```bash
pip install -e ".[dev]"
```

3. Install pre-commit hooks (optional but recommended):
```bash
pre-commit install
```

## Code Style

We use [Ruff](https://github.com/astral-sh/ruff) for linting and formatting.

### Running Linters

```bash
# Check for linting issues
uv run ruff check .

# Auto-fix linting issues
uv run ruff check . --fix

# Check formatting
uv run ruff format --check .

# Auto-format code
uv run ruff format .
```

### Pre-commit Hooks

Pre-commit hooks automatically run linting and formatting before each commit. Install them with:

```bash
pre-commit install
```

## Type Checking

We use [mypy](https://mypy.readthedocs.io/) for type checking (optional for now):

```bash
uv run mypy acestep --ignore-missing-imports
```

## Testing

We use [pytest](https://pytest.org/) for testing:

```bash
# Run all tests
uv run pytest tests/ -v

# Run with coverage
uv run pytest tests/ -v --cov=acestep --cov-report=html
```

## Code Quality Guidelines

1. **Use loguru for logging**: Replace `print()` statements with `logger.info()`, `logger.warning()`, etc.
2. **Handle exceptions properly**: Use specific exception types instead of bare `except:` clauses
3. **Add type hints**: Add type hints to public APIs and new functions
4. **Follow PEP 8**: Use Ruff to enforce style automatically
5. **Keep functions focused**: Split large functions (>50 lines) into smaller, focused functions

## Pull Request Process

1. **Create a branch**: Create a feature branch from `main` or `develop`
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes**: Follow the code style guidelines above

3. **Run checks locally**:
   ```bash
   uv run ruff check .
   uv run ruff format .
   uv run pytest tests/
   ```

4. **Commit your changes**: Write clear, descriptive commit messages
   ```bash
   git commit -m "Add feature: description of changes"
   ```

5. **Push and create PR**: Push your branch and create a pull request on GitHub

6. **Address feedback**: Respond to code review feedback and make necessary changes

## Commit Message Guidelines

- Use present tense: "Add feature" not "Added feature"
- Be descriptive but concise
- Reference issues when applicable: "Fix #123: description"

## Project Structure

- `acestep/` - Main package code
  - `handler.py` - Core model handler
  - `inference.py` - Inference pipeline
  - `api_server.py` - FastAPI server
  - `gradio_ui/` - Gradio UI components
  - `training/` - Training code
- `tests/` - Test files
- `docs/` - Documentation
- `examples/` - Example configurations

## Questions?

If you have questions, please:
- Open an issue on GitHub
- Check existing documentation in `docs/`
- Join our Discord community

Thank you for contributing to ACE-Step!
