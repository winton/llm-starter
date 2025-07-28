# llm

This directory was **copied from** [github.com/winton/llm-starter](https://github.com/winton/llm-starter) and serves as a language-agnostic framework for building software projects with Large Language Model (LLM) tool-use IDEs such as Cursor.

**You are now inside your project**. Follow the workflow below to let the LLM drive documentation, backlog creation, and implementation.

---

## Quick Start

1.  **Describe your idea.**
    Create `PROJECT_DESCRIPTION.md` at the repository root and write a clear, high-level description of what you would like to build (features, requirements, tech stack, constraints, etc.).
2.  **Define project commands.**
    Ensure `llm/llm.config.yaml` specifies the shell commands for testing, linting, formatting, and scans. This is critical for reliable execution.
3.  **Generate the Epic Outline.**
    Open `llm/core/01_create_epic_outline.md` in your chat panel and execute the prompt once. It will create `docs/EPICS.md`, a high-level list of features to build.
4.  **Implement features iteratively.**
    Open `llm/core/02_feature_implementation_loop.md` and run it repeatedly. Each run will pick the next epic, document it, generate tasks, and implement them using a test-driven development cycle until all epics are complete.
5.  **Run periodic maintenance.**
    Execute `llm/core/03_maintenance.md` whenever you finish an epic or want to update the knowledge base and run release checks.

---

## Files & directories created along the way

```
docs/
  EPICS.md                  – high-level feature list (step 3)
epics/
  <epic_slug>/
    outline.md              – just-in-time docs for one epic (step 4)
llm/todos.yaml              – engineering backlog, structured YAML (step 4)
tests/                      – added incrementally by the feature loop
llm/llm.config.yaml         – project-specific commands (step 2)
REVIEW_REQUESTED.md         - created when the LLM needs human help
```

---

## Philosophy

* **Agile, Vertical Slices** – deliver complete, tested features one at a time.
* **Write before you code** – just-in-time docs for each feature prevent rework.
* **Red-green-refactor** – failing tests are written before code, ensuring continuous verification.
* **Small, repeatable steps** – each prompt focuses on a single, atomic activity, keeping the LLM context tight and relevant.

---
## Available Sub-projects

The `llm/projects/` directory contains optional add-on workflows that extend the base system:

* `doc-sync` – keep documentation in sync with code
* `code-health` – unified scan for bugs, security, and refactor opportunities
* `next-feature` – surface high-value new feature ideas

Open a sub-project’s README to see how to run its prompts. Each project only appends TODO objects that flow straight into the shared implementation loop.

---
### Using in Cursor (or any tool-use IDE)

When you execute a prompt:
1. **Add the entire `llm/core/` directory to the chat context.** This gives the LLM all shared loops and conventions.
2. **Add the prompt(s) you actually want to run**—for example, the files in `llm/projects/doc-sync/prompts/`.

Drag the two folders (or multi-select them) into the chat pane, then run. No need to reference individual files; future updates to `llm/core/` will be picked up automatically.