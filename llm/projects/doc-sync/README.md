# Doc-Sync Project

Keep documentation aligned with the codebase.

## Purpose
Detect stale, missing, or inaccurate documentation by comparing source files, public APIs, and the `docs/` folder, then append TODOs (kind=`docs`) to `TODOs.md`.

## Quick Start
1. Open `llm/projects/doc-sync/prompts/01_doc_sync_scan.md` in Cursor.
2. Execute the prompt. If drift is detected, the LLM will append TODO lines to `TODOs.md`.
3. Run the shared code implementation loop (`llm/core/03_code_implementation_loop.md`) to address the generated tasks.

## Output Format
```
Update auth flow doc for new parameters [priority=high, area=docs, estimate=2, project=doc-sync, kind=docs]
```

No code is written by this project; it only updates the backlog. 