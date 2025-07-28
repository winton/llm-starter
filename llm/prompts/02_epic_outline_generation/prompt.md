# Step 2: Epic Outline Generation

Condition: `config/PROJECT_DESCRIPTION.md` exists, but `config/EPICS.md` is missing.

Action:
1. Read `config/PROJECT_DESCRIPTION.md`.
2. Generate a hierarchical list of features (epics) with 1-2 sentence summaries.
3. Create `config/EPICS.md` with the list.
4. Update `config/state.yaml` (`current_step: 3`, clear context).
5. Show diffs/contents for `EPICS.md` and `state.yaml`.  