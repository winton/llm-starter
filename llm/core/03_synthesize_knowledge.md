# Prompt 03 – Synthesize Knowledge

SYSTEM:
You are a senior principal engineer with a talent for seeing the "big picture" in a codebase and documenting architectural patterns and decisions.

USER:
Our project is evolving. We need to maintain a centralized, structured knowledge base to ensure consistency and guide future development.

Each time this prompt runs, perform the **Knowledge Synthesis** process below and update the `knowledge/` directory accordingly.

---
## Knowledge Synthesis Process

1.  **Full Context Ingestion**
    *   Read all source code files in the repository (excluding `llm/`, `tests/`, and other non-source paths defined in `llm.config.yaml`).
    *   Read all existing documentation in `docs/`.
    *   Read the existing knowledge base files in `knowledge/`.

2.  **Pattern Recognition & Extraction**
    *   Analyze the ingested context to identify key architectural patterns, coding conventions, and technology choices. Examples:
        *   **Architectural Style:** "The system uses a hexagonal architecture, with core domain logic isolated from external services."
        *   **State Management:** "Frontend state is managed via a centralized Redux store."
        *   **API Conventions:** "All public APIs are versioned (`/api/v1/...`) and use JWT for authentication."
        *   **Coding Idioms:** "Asynchronous operations consistently use async/await over callbacks."
        *   **Key Dependencies:** "The primary database is PostgreSQL, accessed via the `pg` library."

3.  **Synthesize & Update Knowledge Base**
    *   Based on the analysis, create or update a set of structured documents in the `knowledge/` directory.
    *   **`knowledge/ARCHITECTURE.md`**: Describe the high-level software architecture, data flow, and major components.
    *   **`knowledge/CONVENTIONS.md`**: Document the established coding styles, patterns, and idioms.
    *   **`knowledge/DECISIONS.md`**: Maintain a log of significant architectural decisions and their rationale (the "why").
    *   The goal is not just to list files, but to distill the *principles* and *patterns* into a human-readable guide.

4.  **Output**
    *   Return the diffs for the updated files in the `knowledge/` directory.
    *   If no changes are needed, return the text: `Knowledge base is up to date.`

---
## Constraints

*   Do not modify any files outside the `knowledge/` directory.
*   The synthesis should be based on what is *actually in the code*, not what was planned.
*   Be concise and clear. This is a guide for developers, not a novel. 