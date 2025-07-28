# Doc-Sync Project

Keep documentation aligned with the codebase.

## Purpose
Detect stale, missing, or inaccurate documentation by comparing source files, public APIs, and the `docs/` folder, then append TODOs (kind=`docs`) to `TODOs.md`.

## Quick Start

1. In your IDE (e.g., Cursor) drag **both** folders into the chat pane:  
   • `llm/core/`  
   • `llm/projects/doc-sync/prompts/`
2. Run the chat. The doc-sync scan will append TODOs to `TODOs.md`.
3. Re-run the shared implementation loop (in `llm/core/`) to tackle the new tasks.

## Output Format
```
Update auth flow doc for new parameters [priority=high, area=docs, estimate=2, project=doc-sync, kind=docs]
```

No code is written by this project; it only updates the backlog. 