# Step 4: Test-Driven Feature Implementation

Condition: An actionable task exists in `llm/config/todos.yaml`.

Action:
1. Select task:
   * Identify the first incomplete epic in `llm/config/EPICS.md`.
   * Select the highest-priority `pending` task for that epic from `llm/config/todos.yaml`.
   * If no task is available for the current epic but other epics have tasks, you may proceed with them.
   * If all epics are complete, proceed to Step 5.
   * If no actionable tasks exist at all, return to Step 3.
2. Write failing test:
   * If absent, create `llm/config/epics/<epic_slug>/outline.md`, detailing the plan for this slice.
   * Write the minimum test code required to reproduce a failure for the selected task. It must fail.
   * Output: the diff for the test file(s).
3. Implement code:
   * Write the minimum application code to make the test pass.
   * Run all quality gates defined in `llm/config/gates.yaml`.
   * If gates fail, attempt to fix the code up to three times.
   * If still failing after three attempts, create `llm/config/REVIEW_REQUESTED.md` with the task ID, final diff, and error logs. Output its contents and stop.
   * Output: the diff for the application code.
4. Refactor & update backlog:
   * Optionally refactor the code just written. Re-run tests if you do.
   * Update the task’s `status` to `completed` in `llm/config/todos.yaml`.
   * Output: the diff for `llm/config/todos.yaml` and any refactored source files.
5. Update `llm/config/state.yaml` with:
   * `current_step`: 4 if actionable tasks remain, otherwise 5.
   * `epic_slug`: the current epic slug (or empty if none remain).
   * `task_id`: the ID of the task you just completed (or empty if none remain).
6. Output: the diff for `llm/config/state.yaml`. Stop. 