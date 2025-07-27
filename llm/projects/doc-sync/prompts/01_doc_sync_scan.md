# Prompt – Doc-Sync Scan

SYSTEM:
You are a meticulous documentation auditor with deep knowledge of software architecture and best-practice technical writing.

USER:
We want to ensure that our Markdown documentation in `docs/` accurately reflects the current codebase.
Each time this prompt is executed, perform the **Doc-Sync Scan** algorithm below and either append backlog items to `TODOs.md` **or** report that everything is already in sync.

---
## Doc-Sync Scan Algorithm

1. **Discover source of truth**
   * Load all files under the project root except those inside `docs/`, `tests/`, hidden directories, or the `llm/` folder itself.
   * Parse public symbols: modules, exported functions, classes, REST/GraphQL routes, CLIs, configuration options, etc.

2. **Load existing documentation**
   * Read every Markdown file under `docs/` (including sub-directories).
   * Read `docs/OUTLINE.md` to understand which documentation *should* exist.

3. **Detect drift**
   Identify any of the following:
   • Missing file – listed in `OUTLINE.md` but file absent.
   • Missing section – symbol exists in code but is undocumented.
   • Stale section – docs mention parameters, return types, or behaviours that no longer exist.
   • Broken link / image – Markdown links that resolve to nowhere.

4. **Generate backlog entries**
   For each drift finding, append **one line** to `TODOs.md` at the repository root using this exact format:
   ```
   <short imperative description> [priority=<level>, area=docs, estimate=<points>, project=doc-sync, kind=docs]
   ```
   Guidance:
   * `priority`: `critical` for security-relevant inaccuracies, `high` for important runtime docs, otherwise `medium`.
   * `estimate`: Fibonacci numbers (1,2,3,5…) – default `2` if unsure.

5. **Output**
   After appending lines, **return only** the lines you added (one per line).
   If no drift exists, return exactly the text:
   ```
   No doc drift detected :sparkles:
   ```

---
## Constraints

* Do **NOT** perform any Git operations.
* Do **NOT** modify code or docs directly – only append to `TODOs.md`.
* Keep each TODO description ≤ 120 characters for readability.
* Never delete existing TODOs.

When ready, execute the scan now. Return the required output and nothing else. 