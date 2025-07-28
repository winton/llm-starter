# Step 5: Maintenance & Knowledge Synthesis

!include ../../partials/shared_guidelines.md

Condition: All epics in `config/EPICS.md` are done.

Action:
1. Synthesize knowledge:
   * Scan source code and docs (`config/epics/`, `config/knowledge/`).
   * **If the host repository has a top-level `docs/` folder, reference or link existing documents instead of regenerating duplicates.**
   * Update high-level docs in `config/knowledge/` (`SYSTEM_OVERVIEW.md`, `DATA_MODELS.md`).
   * For any missing ADRs, add one under `config/knowledge/adr/` via `ADR_TEMPLATE.md`.
2. Run health scans:
   * Perform a code health scan (bugs, security, tech debt).
   * Perform a doc-sync scan (documentation drift).
   * Append findings as tasks to `config/todos.yaml` (`project: maintenance`).
3. Show diffs for updated `knowledge/` files and `todos.yaml` (or say `Maintenance complete :sparkles:` if nothing changed).
4. Update `config/state.yaml` (`step`: 4 if actionable `pending` tasks exist in `config/todos.yaml`, otherwise `step`: 5, `epic`: "", `task`: "", `detected`: true).
5. Show diff for `state.yaml`. 