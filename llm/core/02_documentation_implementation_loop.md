# Prompt 02 – Documentation Implementation Loop

SYSTEM:
You are an expert technical writer and software architect.

USER:
We have `docs/OUTLINE.md`, which lists every documentation file that should exist.
Each time this prompt is executed, **repeat the algorithm below**:

1. Load `docs/OUTLINE.md` and build an ordered list of required documentation files.
2. Iterate through that list and find the first entry whose file does **not** yet exist in the repository.
3. Create that missing file with complete, high-quality content and **stop** – do not process subsequent items.
4. If **all** items already exist:
   a. Derive a comprehensive engineering backlog from the documentation and write it to `TODOs.md` at the project root.  
      • Each TODO entry **MUST** include a metadata block in square brackets immediately after the task description, e.g.  
        `Implement user login [priority=critical, area=backend, estimate=5]`  
      • Supported metadata keys: `priority` (`critical`|`high`|`medium`|`low`), `area` (e.g. `frontend`, `backend`, `infra`), `estimate` (story-points or hours), and optional comma-separated `labels`.  
      • The backlog **MUST** be ordered from highest to lowest `priority`; if equal, fall back to appearance order in the docs.
   b. Generate the next prompt `llm/core/03_code_implementation_loop.md` (specification below).
   c. Finish by returning exactly the text `Documentation complete :rocket:`.

---

## Format rules for new documentation files

* Use Markdown.
* Include diagrams, code blocks, or tables where beneficial.
* Keep each file concise yet sufficient for engineers to implement without ambiguity.

---

## Specification for `03_code_implementation_loop.md`

The generated prompt **must instruct the LLM to:**
1. Load `TODOs.md` and parse the metadata on each item (`priority`, `area`, `estimate`, `labels`).
2. Determine the **highest-value** incomplete TODO, preferring (in order):   
   • higher `priority` (`critical` > `high` > `medium` > `low`)  
   • lower `estimate` (faster wins when priorities tie)  
   • oldest creation order as a final tiebreaker.
3. Break the selected TODO into sub-tasks if needed and implement them one by one:
   * Write failing tests first (inside `tests/`).
   * Implement code to make the tests pass.
4. After implementation, run **quality gates**: full test suite, linter, formatter, type-checker, and security scan. If any gate fails, attempt automatic repair; after **4** failed attempts, mark the TODO as `blocked` for human review and pause for assistance (do not attempt any git operations).
5. Perform a **doc-sync check**: compare code changes against documentation. If the docs are outdated, enqueue a follow-up documentation TODO.
6. Persist new architectural decisions to `knowledge/DECISIONS.md` so subsequent loops can load them quickly.
7. Update `TODOs.md` – mark completed items or remaining sub-tasks accordingly.
8. **Stop** after finishing the current sub-task or TODO, never deleting uncommitted or modified files without explicit user approval.

Return ONLY the content of the file you created or updated during this run. 