# Step 1: Project Initialization

Condition: `llm/config/PROJECT_DESCRIPTION.md` does not exist.

Action:
1. Ask the operator for:
   a. A concise, high-level description of the project.  
   b. (If not obvious) any additional context needed to determine the project’s primary language and framework.
2. Create or initialize the following files:
   * `llm/config/PROJECT_DESCRIPTION.md` with the description.
   * Create or update `llm/config/gates.yaml`, replacing placeholder values with generated shell commands for the quality gates (`test`, `lint`, `format`, `type_check`, `security_scan`).
   * `llm/config/todos.yaml` initializing it as an empty list (`[]`) if it does not yet exist.
3. Write or update `llm/config/state.yaml` setting `current_step: 2` and clearing any `epic_slug` or `task_id` fields.
4. Output: the full contents of `llm/config/PROJECT_DESCRIPTION.md`, `llm/config/gates.yaml`, `llm/config/todos.yaml`, and the diff for `llm/config/state.yaml`. Stop. 