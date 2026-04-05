---
name: readme-updater
description: Updates the project's README.md with comprehensive, up-to-date documentation including descriptions, installation instructions, execution steps, and examples. Use this when the user asks to update project documentation or README details.
---

# README Updater Skill

When the project undergoes structural or feature changes, or when specifically requested, you MUST ensure that the `README.md` accurately reflects the current state of the project.

## Instructions

1. **Analyze Project State**: First, review the project's file structure, configuration/dependency files (e.g., `pyproject.toml`, `requirements.txt`), and main entry points to understand what the project does and what commands operate it.
2. **File Update**: Locate or create the `README.md` file in the root directory.
3. **Maintain Required Sections**: Restructure or write the `README.md` so that it always includes the following well-defined sections:
   - **Title and Description**: A high-level, clear explanation of the project's purpose and functionality.
   - **Installation / Deployment**: Step-by-step instructions on how to install necessary dependencies or deploy the project from scratch. Include prerequisites if necessary.
   - **Running the Application**: Exact instructions and commands to execute the project or start the server natively.
   - **Usage Examples & Commands**: Practical terminal commands or code snippet examples demonstrating how users can interact with the given tools or APIs.
4. **Accuracy & Context**: Cross-reference any scripts or terminal commands you document to ensure they physically exist in the project and are completely correct.

## Example Formatting

```markdown
# [Project Name]

[Brief description of the project detailing the problem it solves and its main functionalities.]

## Prerequisites

List any system requirements.
- Python 3.12+

## Installation & Deployment

Instructions on how to install and prepare the environment.

\`\`\`bash
pip install -r requirements.txt
# or
poetry install
\`\`\`

## Running the Application

To run the application locally:

\`\`\`bash
python src/main.py
\`\`\`

## Usage Examples

Below are a few examples of how to run specific commands:

\`\`\`bash
# Example running the linter
flake8 .

# Example running tests
pytest tests/
\`\`\`
```
