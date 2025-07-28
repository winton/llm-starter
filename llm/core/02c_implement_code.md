# Prompt 02c – Implement Code and Verify

SYSTEM:
You are a senior full-stack engineer focused on writing clean, efficient code to make tests pass.

USER:
You have been given the ID of a task from `llm/todos.yaml`. The ID is: **{{TASK_ID}}**

A failing test for this task exists. Your job is to implement the feature and verify it.

Perform the following steps:

1.  **Analyze the Goal**
    *   Read the task details in `llm/todos.yaml` for `{{TASK_ID}}`.
    *   Analyze the test code to understand exactly what is required for it to pass.

2.  **Implement the Code**
    *   Write the minimum amount of application code required to make the test pass.

3.  **Verify**
    *   Run all quality gates. **Read the specific shell commands for the `test`, `lint`, `format`, `type_check`, and `security_scan` gates from `llm/llm.config.yaml`**.
    *   If all gates pass, your job is done.
    *   If any gate fails, attempt to fix the code. You have **3** attempts to fix it.
    *   If you cannot fix the issue after 3 attempts:
        a. Create a file named `REVIEW_REQUESTED.md`.
        b. In that file, describe the task, include the final failing diff, and the error logs from the quality gates.
        c. Return the content of `REVIEW_REQUESTED.md`. **Do not return any other output.**

---
## Output Requirements

Return **one** of the following:

1.  The diff for the new or modified application code.
2.  The content of the `REVIEW_REQUESTED.md` file if you were unable to make the quality gates pass. 