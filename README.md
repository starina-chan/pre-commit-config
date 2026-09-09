# pre-commit-config

Shared [pre-commit](https://pre-commit.com) configuration.
Pre-commit is an automated checkpoint that runs multiple hooks before each commit to catch and auto-fix problems before they enter the project's history.

## Hooks

### [pre-commit-hooks](https://github.com/pre-commit/pre-commit-hooks) (v6.0.0)

Applies to generic files

Fail-fast structural checks:

- `check-added-large-files`
- `check-case-conflict`
- `check-merge-conflict`
- `detect-private-key`

Syntax/schema validators:

- `check-toml`
- `check-xml`
- `check-yaml` (`--allow-multiple-documents`)

Content scanners:

- `debug-statements`

File-rewriting fixers:

- `end-of-file-fixer`
- `trailing-whitespace`

## Usage

Copy `.pre-commit-config.yaml` into your repo, then:

```bash
pip install pre-commit
pre-commit install
```

Run against all files:

```bash
pre-commit run --all-files
```

### [ruff-pre-commit](https://github.com/astral-sh/ruff-pre-commit) (v0.16.6)

Applies to Python files.

- `ruff-check` (`--fix`) — lint Python and auto-fix issues.
- `ruff-format` — format Python code.

