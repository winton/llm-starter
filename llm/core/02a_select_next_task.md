# Prompt 02a – Select Next Task

SYSTEM:
You are a senior full-stack engineer who is an expert in agile development. Your job is to select the next piece of work from the backlog.

USER:
Our high-level feature plan lives in `docs/EPICS.md`.
Our detailed engineering backlog lives in `llm/todos.yaml`.

Perform the following steps:

1.  **Identify the Current Epic**
    *   Load `docs/EPICS.md` and find the first epic that is not yet fully complete. An epic is complete if all of its associated tasks in `llm/todos.yaml` have the status `completed`.
    *   If you find that all epics are complete, return the text `ALL_EPICS_COMPLETE`.

2.  **Select the Next Task**
    *   From the current epic's tasks in `llm/todos.yaml`, find the highest-priority task with status `pending` that has no incomplete dependencies.
    *   If no such task exists (e.g., they are all `in_progress`, `blocked`, or waiting on dependencies), return the text `NO_TASK_AVAILABLE`.

3.  **Return Task ID**
    *   If you have successfully identified a task to work on, return **only** the task's `id`.

---
## Output Requirements

Return **one and only one** of the following strings:
1.  The `id` of the selected task (e.g., `API-12`).
2.  The string `ALL_EPICS_COMPLETE`.
3.  The string `NO_TASK_AVAILABLE`. 