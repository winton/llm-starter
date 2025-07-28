# llm-starter

A minimal, language-agnostic scaffold for Large Language Model (LLM)-assisted development.

This repository’s **only job** is to provide the `llm/` directory. Drop that folder into any new or existing codebase and you’re ready to drive the project via prompts in a tool-use IDE such as Cursor.

---
## Installation

1.  **Clone or download this repo** (do *not* initialise it as a sub-module—you only need the files once).

    ```bash
    git clone https://github.com/winton/llm-starter.git
    ```

2.  **Copy the `llm/` directory** (and nothing else) into the root of your target project:

    ```bash
    cp -R llm-starter/llm yourproject/
    ```

3.  **Commit the files** inside your own project’s repository.

4.  Open the project in Cursor (or another tool-use IDE), add `llm/prompts/prompt.md` to the chat context, and say "continue". **The framework will auto-detect your stack and generate sensible defaults—no manual setup needed.**

---
## Updating `llm/`

Future improvements to the framework will appear in this repo. To upgrade, simply replace the `llm/prompts` folder in your project with the latest version from `main` and commit the changes:

    ```bash
    rm -rf yourproject/llm/prompts
    cp -R llm-starter/llm/prompts yourproject/llm/
    ```

---
## License

MIT 