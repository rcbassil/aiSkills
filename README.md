# Gemini Skills

A curated collection of reusable agent skills for the `.agent/skills` framework. Each skill encapsulates a focused capability — from formatting commit messages to generating Pydantic models — that an AI coding assistant can invoke on demand inside any workspace.

## Included Skills

| Skill | Description |
|---|---|
| **changelog-tracker** | Manages and tracks `CHANGELOG.md` updates following the [Keep a Changelog](https://keepachangelog.com/) format. |
| **code-reviewer** | Reviews code changes for quality, readability, maintainability, and best-practice conformity. |
| **git-commit-formatter** | Generates commit messages that follow the [Conventional Commits](https://www.conventionalcommits.org/) specification. |
| **json-to-pydantic** | Converts raw JSON snippets into structured Python Pydantic data models. |
| **license-header-adder** | Appends the standard Apache 2.0 license header to new source files. |
| **readme-updater** | Keeps `README.md` accurate and up-to-date whenever the project changes. |

## Prerequisites

- **Python** 3.13+
- [**uv**](https://github.com/astral-sh/uv) (recommended) or pip

## Installation

```bash
git clone https://github.com/rcbassil/aiSkills.git
cd aiSkills

# Using uv (recommended)
uv sync

# Using pip
pip install .
```

## Running the Application

```bash
# Using uv
uv run main.py

# Using python directly
python main.py
```

Expected output:

```
Hello from aiSkills!
```

## Usage Examples

Skills are activated by communicating your intent to the agent inside your workspace. For example:

```text
"Update the README"            → triggers readme-updater
"Commit these changes"         → triggers git-commit-formatter
"Review my code"               → triggers code-reviewer
"Document project changes"     → triggers changelog-tracker
"Convert this JSON to a model" → triggers json-to-pydantic
```

## Project Structure

```
.
├── .agent/skills/       # Skill definitions (SKILL.md + resources per skill)
├── src/agent/           # Python package source
├── tests/               # Test suite
├── docs/                # Documentation
├── main.py              # Entry point
├── pyproject.toml       # Project metadata & dependencies
├── CHANGELOG.md         # Project changelog
└── LICENSE              # Apache License 2.0
```

## License

This project is licensed under the [Apache License 2.0](LICENSE).
