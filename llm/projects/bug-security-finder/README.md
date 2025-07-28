# Bug & Security Finder Project

Locate defects and vulnerabilities automatically.

## Purpose
Scan source code and dependency manifests to flag bugs (`kind=bugfix`) or security issues (`kind=security`). Adds corresponding TODOs to `TODOs.md`.

## Quick Start

1. Drag `llm/core/` plus `llm/projects/bug-security-finder/prompts/` into your chat.
2. Run the scan prompt; findings will be appended to `TODOs.md`.
3. Core loop will handle fixes on the next run.

## Output Example
```
Upgrade bcrypt to v4 to fix CVE-2023-1234 [priority=critical, area=backend, estimate=1, project=bug-security-finder, kind=security]
``` 