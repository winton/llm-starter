# llm

This directory was **copied from** [github.com/winton/llm-starter](https://github.com/winton/llm-starter) and serves as a language-agnostic framework for building software projects with Large Language Model (LLM) tool-use IDEs such as Cursor.

**You are now inside your project**. Follow the workflow below to let the LLM drive documentation, backlog creation, and implementation.

---

## Quick Start

1. **Describe your idea.**
   Create `PROJECT_DESCRIPTION.md` at the repository root and write a clear, high-level description of what you would like to build (features, requirements, tech stack, constraints, etc.).
2. **Generate an outline.**
   Open `llm/core/01_create_documentation_outline.md` in your chat panel and execute the prompt once. It will create `docs/OUTLINE.md`, a table-of-contents for all required documentation files.
3. **Fill in the docs.**
   Open `llm/core/02_documentation_implementation_loop.md` and run it repeatedly. Each run will create the *next* missing document from the outline until the set is complete.
4. **Produce the engineering backlog.**
   On its final run the documentation loop writes `TODOs.md` (a backlog) and generates the next prompt `llm/core/03_code_implementation_loop.md`.
5. **Implement the code.**
   Run `03_code_implementation_loop.md` iteratively. The LLM will pick the highest-priority TODO, write tests, implement code, and repeat until all tasks are finished and the test suite passes.

---

## Files & directories created along the way

```
docs/
  OUTLINE.md                – generated in step 2
  <other docs>.md           – generated in step 3
TODOs.md                    – engineering backlog (step 4)
tests/                      – added incrementally by the code loop
```

---

## Philosophy

* **Write before you code** – comprehensive docs prevent re-work.
* **Red-green-refactor** – failing tests are written before code, ensuring continuous verification.
* **Small, repeatable steps** – each prompt focuses on a single, atomic activity, keeping the LLM context tight and relevant.

---
## Available Sub-projects

The `llm/projects/` directory contains optional add-on workflows that extend the base system:

* `doc-sync` – keep documentation in sync with code
* `next-feature` – surface high-value new feature ideas
* `bug-security-finder` – discover bugs and security issues
* `refactor-helper` – propose safe refactors to reduce technical debt

Open a sub-project’s README to see how to run its prompts. Each project only appends TODO lines that flow straight into the shared implementation loop in `llm/core/03_code_implementation_loop.md`.
