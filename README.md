# Custom Agent

Custom Agent is a Python project designed to provide and manage a suite of specialized agent skills via the `.agent/skills` framework. 

The currently included skills enhance your project workspace organically:
- **Changelog Tracker**: Standardizes and manages `CHANGELOG.md` updates.
- **Code Reviewer**: Automates detailed code reviews based on best practices.
- **Git Commit Formatter**: Generates compliant Conventional Commit logs.
- **License Header Adder**: Appends legal licensing text to top of new files.
- **README Updater**: Automatically handles maintaining this very documentation.

## Prerequisites

- **Python:** version 3.13 or higher.

## Installation & Deployment

Currently, the project focuses on these native agent capabilities and requires no complex third-party dependencies from `pyproject.toml`.

To spin it up, just clone and enter the repository:

```bash
git clone <your-repo-url>
cd geminiSkills
```

If dependencies are added in the future, you can resolve them natively via pip from the `pyproject.toml` file:

```bash
pip install .
```

## Running the Application

The main execution points to a straightforward entry script. To run it locally:

```bash
python main.py
```

## Usage Examples & Commands

To test the main module output, you can use:

```bash
python main.py
# Output: Hello from customagent!
```

To invoke any of the active skills, communicate your intent to the agent within the workspace context. For instance:
- *"update the README"*
- *"Commit these changes"*
- *"Please document project changes"*
- *"Review my code"*
