# Step 5: Maintenance & Knowledge Synthesis

Condition: All epics in `llm/config/EPICS.md` are complete.

Action:
1. Synthesize knowledge:
   * Scan all source code and docs (`llm/config/epics/`, `llm/config/knowledge/`).
   * Update or create high-level documentation in `llm/config/knowledge/` (`SYSTEM_OVERVIEW.md`, `DATA_MODELS.md`).
   * If you discover undocumented architectural decisions, create an ADR in `llm/config/knowledge/adr/` using `ADR_TEMPLATE.md`. (template is in this folder)
2. Run health scans:
   * Perform a code health scan (bugs, security, tech debt).
   * Perform a doc-sync scan (documentation drift).
   * Append any findings as tasks to `llm/config/todos.yaml` with `project` set to `maintenance`.
3. Output:
   * Diffs for any files in `llm/config/knowledge/`.
   * The YAML diff for any tasks added to `llm/config/todos.yaml`.
   * If no changes were made, output: `Maintenance complete :sparkles:`.
4. Update `llm/config/state.yaml` setting `current_step: 5` and clearing `epic_slug` and `task_id`.
5. Output: the diff for `llm/config/state.yaml`. Stop. 