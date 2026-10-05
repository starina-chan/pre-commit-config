# pre-commit-config

Shared [pre-commit](https://pre-commit.com) configuration.
Pre-commit is an automated checkpoint that runs multiple hooks before each commit to catch and auto-fix problems before they enter the project's history.

## Installation

Install [uv](https://docs.astral.sh/uv/getting-started/installation/), then install pre-commit as a uv tool:

```bash
uv tool install pre-commit
```

Don't install pre-commit with apt.
Ubuntu 22.04 ships pre-commit 2.17.0, but `pre-commit-hooks` v6.0.0 requires 3.2.0 or later.

Clone this repo once per machine:

```bash
git clone https://github.com/starina-chan/pre-commit-config.git ~/pre-commit-config
```

## Usage

From the root of each repo, copy the config, install the git hook and commit the config:

```bash
cp -i ~/pre-commit-config/.pre-commit-config.yaml .
pre-commit install
git add .pre-commit-config.yaml
git commit -m "build: add pre-commit config"
```

Run once against all existing files:

```bash
pre-commit run --all-files
```

To pick up later changes to this config, pull this repo and copy the file again:

```bash
git -C ~/pre-commit-config pull
cp -i ~/pre-commit-config/.pre-commit-config.yaml .
```

## Hooks

### [pre-commit-hooks](https://github.com/pre-commit/pre-commit-hooks) (v6.0.0)

Applies to generic files

**Fail-fast structural checks:**

- `check-added-large-files`
- `check-case-conflict`
- `check-merge-conflict`
- `detect-private-key`

**Syntax/schema validators:**

- `check-toml`
- `check-xml`
- `check-yaml` (`--allow-multiple-documents`)

**Content scanners:**

- `debug-statements`

**File-rewriting fixers:**

- `end-of-file-fixer` (skips `.pgm`)
- `trailing-whitespace` (skips `.pgm`)

Binary `.pgm` maps (ROS map_server) are excluded, since these fixers
would append a byte to the pixel data.

### [ruff-pre-commit](https://github.com/astral-sh/ruff-pre-commit) (v0.16.6)

Applies to Python files.

- `ruff-check` (`--fix`) — lint Python and auto-fix issues.
- `ruff-format` — format Python code.
