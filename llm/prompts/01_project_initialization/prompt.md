# Step 1: Project Initialization

Condition: Any of these files is missing:
* `config/PROJECT_DESCRIPTION.md`
* `config/gates.yaml`
* `config/todos.yaml`

Action:
1. If `PROJECT_DESCRIPTION.md` is missing, ask the operator for:
   a. A concise, high-level project description.  
   b. (If not obvious) the primary language / framework.
2. For each file above that is missing, create it:
   * `PROJECT_DESCRIPTION.md` – write the description.
   * `gates.yaml` – generate shell commands for `test`, `lint`, `format`, `type_check`, `security_scan`.
   * `todos.yaml` – initialize to an empty list (`[]`).
3. Update `config/state.yaml` (`current_step: 2`, clear `epic_slug`, `task_id`).
4. Show diffs/contents of the files you created or changed. 