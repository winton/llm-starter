# Refactor Helper Project

Identify and queue maintainability improvements.

## Purpose
Analyse the codebase for complexity, duplication, or outdated patterns and add refactor tasks (`kind=refactor`) to `TODOs.md`.

## Quick Start

1. Drag `llm/core/` together with `llm/projects/refactor-helper/prompts/` into the chat.
2. Execute. The finder will add refactor TODOs to the backlog.
3. Run the core loop to implement them when capacity allows.

## Output Example
```
Extract date utilities into dedicated module [priority=medium, area=backend, estimate=3, project=refactor-helper, kind=refactor]
``` 