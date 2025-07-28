# Next-Feature Ideation Project

Continuously suggest high-value product improvements.

## Purpose
Analyse existing documentation, backlog, and knowledge base to propose new feature ideas and add them to `llm/todos.yaml`.

## Quick Start

1. Drag the `llm/core/` folder **and** `llm/projects/next-feature/prompts/` into the chat context.
2. Execute. The ideator will add up to three feature TODOs.
3. Let the core implementation loop tackle them in priority order.

## Output Example
```yaml
- id: FEAT-22
  content: Add dark-mode toggle
  priority: medium
  area: frontend
  estimate: 8
  project: next-feature
  kind: feature
``` 