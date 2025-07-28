# Step 3: Backlog Seeding

Condition: `llm/config/EPICS.md` exists, but `llm/config/todos.yaml` is empty or contains no actionable tasks. An actionable task is one with status `pending` and no incomplete dependencies.

Action:
1. Read `llm/config/EPICS.md` to understand the roadmap.
2. Brainstorm up to three high-value, concrete feature tasks that would advance the first incomplete epic.
3. For each task, create a YAML object following the schema in `BACKLOG_SCHEMA.md` (located in this folder). Assign a fresh ID (e.g., `FEAT-1`), set `project` to `core`, `kind` to `feature`.
4. Append the task objects to `llm/config/todos.yaml`.
5. Write or update `llm/config/state.yaml` with `current_step: 4`, setting `epic_slug` to the epic you just advanced, and clearing `task_id`.
6. Output: the YAML diff for `llm/config/todos.yaml` and the diff for `llm/config/state.yaml`. Stop. 