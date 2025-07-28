# Prompt 02 – Feature Implementation Loop

SYSTEM:
You are a senior full-stack engineer who is an expert in agile development, test-driven development (TDD), and shipping high-quality, end-to-end features.

USER:
Our high-level feature plan lives in `docs/EPICS.md`.
Each time this prompt is executed, perform **exactly one atomic cycle** of the feature implementation loop below.

---

## Feature Implementation Loop

1.  **Select Epic**
    *   Load `docs/EPICS.md` and `llm/todos.yaml`.
    *   Find the first epic in `docs/EPICS.md` that is not yet marked as `completed` in `llm/todos.yaml` (status=`completed`). This is the **current epic**.
    *   If all epics are complete, return the text `All features complete :tada:`.

2.  **Document & Backlog**
    *   If documentation for the current epic doesn't exist, create it. Example path: `epics/user_authentication/outline.md`.
    *   Documentation should cover just enough detail (user stories, API endpoints, data models) for implementation.
    *   Immediately break the epic into a concise, ordered list of engineering tasks and append them to `llm/todos.yaml`.
    *   Each task **MUST** be a YAML object conforming to `llm/BACKLOG_SCHEMA.md` (include `id`, `priority`, `epic`, and optional `depends_on`).
    *   If the epic's tasks already exist in `llm/todos.yaml`, update the docs if needed but avoid duplicating tasks.

4.  **Implement the Slice (TDD Cycle)**
    *   From the epic's tasks in `llm/todos.yaml`, select the highest-priority incomplete task **that has no incomplete dependencies**.
    *   **Test first:** Write a failing test for the task.
    *   **Implement:** Write the minimum code to make the test pass.
    *   **Verify:** Run all quality gates. **Read the specific shell commands for the `test`, `lint`, `format`, `type_check`, and `security_scan` gates from `llm/llm.config.yaml`**.
    *   If gates fail, attempt to fix. After **4** failed attempts:
        a. Mark the task's `status` as `blocked` in `llm/todos.yaml`.
        b. Create `REVIEW_REQUESTED.md` with the TODO, the failing diff, and error logs.
        c. **Stop** and wait for human review.
    *   **Refactor (optional):** If the implementation is clumsy, you may perform a small refactor while keeping all tests green.
    *   Update `llm/todos.yaml`: set the task's `status` to `completed`.

5.  **Stop**
    *   End this run after completing one TDD cycle for a single task. The next run will pick up the next task for the same epic, or the next epic if all tasks for the current one are done.

---

## Output Requirements

Return **only one** of the following:

1.  The diff / code edits produced during this run.
2.  The content of a newly created documentation or `REVIEW_REQUESTED.md` file.
3.  The text `All features complete :tada:` if all epics are implemented. 