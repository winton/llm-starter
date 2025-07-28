# Prompt 04 – Release Prep

SYSTEM:
You are a release manager responsible for ensuring that completed features are stable, secure, well-documented, and free of technical debt before they are deployed.

USER:
A feature epic has just been completed (all its TODOs are done). Before we consider it "shipped," we need to run a full release-preparation checklist.

Execute the **Release Prep Sequence** below.

---
## Release Prep Sequence

1.  **Run Refactor Helper**
    *   Execute the prompt in `llm/projects/refactor-helper/prompts/01_refactor_candidate_finder.md`.
    *   This will scan the newly added code for any cleanup opportunities (e.g., complexity, duplication).
    *   The output will be new `kind=refactor` tasks added to `TODOs.md`.

2.  **Run Bug & Security Finder**
    *   Execute the prompt in `llm/projects/bug-security-finder/prompts/01_bug_security_scan.md`.
    *   This performs a final sweep for any bugs or vulnerabilities introduced.
    *   The output will be new `kind=bugfix` or `kind=security` tasks added to `TODOs.md`.

3.  **Run Doc-Sync**
    *   Execute the prompt in `llm/projects/doc-sync/prompts/01_doc_sync_scan.md`.
    *   This ensures that all documentation for the feature is accurate and up-to-date with the final code.
    *   The output will be new `kind=docs` tasks added to `TODOs.md`.

4.  **Implement Fixes**
    *   The main implementation loop (`llm/core/02_feature_implementation_loop.md`) should now be run.
    *   It will automatically pick up and implement all the `refactor`, `bugfix`, `security`, and `docs` tasks that were just created.
    *   Continue running the main loop until all these release-prep tasks are complete.

5.  **Generate Changelog**
    *   Once the backlog is clear, analyze the git history for the completed epic.
    *   Generate a summary of the changes in a format suitable for `CHANGELOG.md`.

---
## Output

Return a summary of the actions taken, for example:
```
Release prep for epic 'User Authentication' initiated.
- Refactor scan: 2 tasks added.
- Security scan: 1 critical issue found.
- Doc-sync: 3 docs tasks added.
Proceed by running the main implementation loop to clear the backlog.
``` 