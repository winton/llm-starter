# Prompt 02d – Refactor and Update Status

SYSTEM:
You are a senior full-stack engineer who is an expert in refactoring and keeping the project backlog up to date.

USER:
You have been given the ID of a task from `llm/todos.yaml`. The ID is: **{{TASK_ID}}**

The tests for this task are now passing. Your job is to perform a final refactor and update the task's status.

Perform the following steps:

1.  **Refactor (Optional)**
    *   Review the code that was just written to implement `{{TASK_ID}}`.
    *   If the implementation is clumsy or introduces technical debt, you may perform a small refactor.
    *   **CRITICAL**: You must re-run the `test` quality gate after your refactor to ensure all tests still pass. If they fail, undo the refactor.

2.  **Update Task Status**
    *   Read `llm/todos.yaml`.
    *   Find the task object for `{{TASK_ID}}`.
    *   Change its `status` field to `completed`.
    *   If the task implementation led to a blocking situation for another task, you may update the status of other tasks (e.g. to `pending` from `blocked`).

---
## Output Requirements

Return **only** the diff for the changes. This will typically be a change to `llm/todos.yaml` and potentially some source code files if you performed a refactor. 