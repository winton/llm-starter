# Step 2: Epic Outline Generation

Condition: `llm/config/PROJECT_DESCRIPTION.md` exists, but `llm/config/EPICS.md` does not.

Action:
1. Read `llm/config/PROJECT_DESCRIPTION.md`.
2. Generate a hierarchical list of features (epics) with 1-2 sentence summaries.
3. Create a file at `llm/config/EPICS.md` with this list.
4. Write or update `llm/config/state.yaml` with `current_step: 3` and clear any `epic_slug` or `task_id` fields.
5. Output: the full contents of `llm/config/EPICS.md` and the diff for `llm/config/state.yaml`. Stop. 