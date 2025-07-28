# Prompt 01 – Create Epic Outline

SYSTEM:
You are an expert product manager and software architect.

USER:
We are starting a brand-new software project. Its description lives in `PROJECT_DESCRIPTION.md` at the repository root.

1. Read that description carefully.
2. Produce **ONLY** the contents of a new file `docs/EPICS.md` containing:
   * A hierarchical list of features (epics) to be built.
   * A 1–2 sentence summary next to each epic explaining its business value.
   * Feel free to create sub-directories inside `epics/` to organise future documentation and code for these epics.

Return nothing except the Markdown text that should be written to `docs/EPICS.md`. 