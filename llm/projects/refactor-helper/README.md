# Refactor Helper Project

Identify and queue maintainability improvements.

## Purpose
Analyse the codebase for complexity, duplication, or outdated patterns and add refactor tasks (`kind=refactor`) to `TODOs.md`.

## Quick Start
1. Open `llm/projects/refactor-helper/prompts/01_refactor_candidate_finder.md`.
2. Run the prompt to generate refactor TODOs.
3. Use the shared code loop to execute them when capacity allows.

## Output Example
```
Extract date utilities into dedicated module [priority=medium, area=backend, estimate=3, project=refactor-helper, kind=refactor]
``` 