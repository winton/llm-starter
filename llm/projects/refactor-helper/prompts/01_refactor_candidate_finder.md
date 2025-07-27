# Prompt – Refactor Candidate Finder

SYSTEM:
You are a code-quality analyst skilled at recognising technical-debt hotspots and refactor opportunities.

USER:
We’d like to keep the codebase healthy. Each time this prompt runs, analyse the project, suggest a handful of valuable refactors, append them to the backlog, and stop.

---
## Refactor Discovery Algorithm

1. **Scan the codebase**
   * Inspect all source files (exclude `docs/`, `tests/`, `llm/`, hidden folders).
   * Flag:
     • Files > 400 lines.
     • Functions/methods > 40 lines or cyclomatic complexity > 10.
     • Duplicate code blocks > 20 lines appearing in ≥2 places.
     • Outdated patterns (e.g., callbacks instead of async/await, class components instead of hooks).
     • TODO/FIXME comments lingering > 30 days (if datestamped).

2. **Prioritise**
   * Rank findings by risk and maintenance cost.
   * Assign `priority`: `high` if blocking new work or causes frequent bugs, else `medium`.
   * Estimate effort (Fibonacci 2,3,5,8) – default 3.

3. **Write backlog entries**
   Append one line per finding to `TODOs.md`:
   ```
   <imperative description> [priority=<level>, area=<file/dir>, estimate=<pts>, project=refactor-helper, kind=refactor]
   ```
   Keep description ≤120 characters.

4. **Output**
   Return only the lines you added (one per line). If the codebase is already tidy, return exactly:
   ```
   No refactor opportunities found :sparkles:
   ```

---
## Constraints

* No Git operations or direct code edits.
* Never delete or modify existing TODOs.
* Avoid duplicating tasks already present in `TODOs.md`.

Execute the algorithm now and output the required lines only. 