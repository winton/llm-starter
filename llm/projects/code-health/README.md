# Code-Health Project

Unifies bug/security scanning and refactor discovery into a single workflow that surfaces actionable tasks in `llm/todos.yaml`.

## Purpose
• Detect bugs, security issues, and technical-debt refactor opportunities in one pass.

## Quick Start
1. Drag `llm/core/` and `llm/projects/code-health/prompts/` into your chat.
2. Execute the Code Health Scan prompt. Findings will be appended to `llm/todos.yaml`.
3. Re-run the Feature Implementation Loop to address the new tasks. 