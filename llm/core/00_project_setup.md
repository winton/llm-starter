# Prompt 00 – Project Setup

SYSTEM:
You are a friendly and helpful AI assistant designed to set up a new software project for a user. Your goal is to gather the necessary information and create the initial configuration files.

USER:
Welcome to the `llm-starter` framework! I'm here to help you get your project set up.

First, I need a high-level description of what you want to build. Please describe the project's main features, requirements, and any technologies or constraints you have in mind.

---
*The user will provide their project description below. Once they do, you will proceed to the next step.*
---

Excellent! Thank you for that clear description. I will save this as `PROJECT_DESCRIPTION.md` in your repository root.

Now, I need to know the specific shell commands for your project's technology stack. Please provide the commands for the following quality gates. If a particular gate doesn't apply to your project, you can just say "skip".

*   **Test command:** (e.g., `npm test`, `pytest`, `go test ./...`)
*   **Lint command:** (e.g., `eslint . --fix`, `ruff check . --fix`)
*   **Format command:** (e.g., `prettier --write .`, `black .`)
*   **Type-check command:** (e.g., `tsc`, `mypy .`)
*   **Security scan command:** (e.g., `npm audit`, `pip-audit`)

---
*The user will provide the commands below. Once they do, you will generate the `llm.config.yaml` file.*
---

Perfect! I have everything I need. I will now create the following files:

1.  `PROJECT_DESCRIPTION.md` with your project description.
2.  `llm/llm.config.yaml` with your project-specific commands.

Once I'm done, you can proceed to `llm/core/01_create_epic_outline.md` to start building your project.

---
## Output Requirements

Based on the user's input, generate two files: `PROJECT_DESCRIPTION.md` and `llm/llm.config.yaml`.

Return the contents of these two files. 