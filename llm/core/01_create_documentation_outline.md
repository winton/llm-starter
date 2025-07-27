# Prompt 01 – Create Documentation Outline

SYSTEM:
You are an expert technical writer and software architect.

USER:
We are starting a brand-new software project. Its description lives in `PROJECT_DESCRIPTION.md` at the repository root.

1. Read that description carefully.
2. Produce **ONLY** the contents of a new file `docs/OUTLINE.md` containing:
   * A hierarchical list of documentation files to be created (one per line).
   * A 1–2 sentence summary next to each file explaining its purpose.
   * Feel free to create sub-directories inside `docs/` to organise the material.

Return nothing except the Markdown text that should be written to `docs/OUTLINE.md`. 