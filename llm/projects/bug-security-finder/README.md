# Bug & Security Finder Project

Locate defects and vulnerabilities automatically.

## Purpose
Scan source code and dependency manifests to flag bugs (`kind=bugfix`) or security issues (`kind=security`). Adds corresponding TODOs to `TODOs.md`.

## Quick Start
1. Open `llm/projects/bug-security-finder/prompts/01_bug_security_scan.md`.
2. Execute the prompt to populate the backlog with findings.
3. Let the shared code loop tackle each issue in priority order.

## Output Example
```
Upgrade bcrypt to v4 to fix CVE-2023-1234 [priority=critical, area=backend, estimate=1, project=bug-security-finder, kind=security]
``` 