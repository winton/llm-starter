# Agents Overview
_Generated: 2025-07-30T12:00:00Z_

## Agents
| id | summary | input | calls |
| -- | ------- | ----- | ----- |
| agent-gen | convert a raw prompt into a compliant agent file | raw_prompt | none |
| agent-list-planner | break a user goal into a minimal set of micro-agents | goal | none |
| agents-catalog | maintain llm/agents.md overview of all agents | none | none |
| architectural-reviewer | evaluate architectural impact and maintain system integrity | diff | ledger-clerk |
| code-implementer | implement code to satisfy a ticket and pass all gates | ticket | lint-gatekeeper, security-scanner, test-author, ledger-clerk |
| context-gatherers | capture user vision and domain knowledge before planning begins | goals | none |
| doc-coverage-checker | verify that all changed public symbols are documented | diff | doc-updater, ledger-clerk |
| doc-updater | keep documentation accurate after code changes | diff | doc-coverage-checker, lint-gatekeeper, ledger-clerk |
| ledger-clerk | append structured, timestamped entries to project ledgers | entry | none |
| lint-gatekeeper | block merges with style or formatting violations | diff | ledger-clerk |
| merge-arbiter | gatekeeper that merges PRs only when all required checks pass | pr-status | ledger-clerk |
| planning-tasking | slice requirements into atomic tickets with dependencies | requirements, acceptance-criteria, risks | none |
| problem-opportunity-shapers | distill clarified goals into scored problems & opportunities | objectives, domain-insights | none |
| scope-requirement-writers | translate chosen solution into clear scope, requirements & risks | winners, solution-variants | none |
| security-scanner | scan diffs for vulnerabilities, secrets, and insecure patterns | diff | ledger-clerk |
| solution-designers | craft and vet solution variants for scored opportunities | pain-points, opportunities | none |
| test-author | generate or update automated tests for a given code change | diff | lint-gatekeeper, ledger-clerk |

```mermaid
graph TD
  architectural-reviewer --> ledger-clerk
  code-implementer --> lint-gatekeeper
  code-implementer --> security-scanner
  code-implementer --> test-author
  code-implementer --> ledger-clerk
  doc-coverage-checker --> doc-updater
  doc-coverage-checker --> ledger-clerk
  doc-updater --> doc-coverage-checker
  doc-updater --> lint-gatekeeper
  doc-updater --> ledger-clerk
  lint-gatekeeper --> ledger-clerk
  merge-arbiter --> ledger-clerk
  security-scanner --> ledger-clerk
  test-author --> lint-gatekeeper
  test-author --> ledger-clerk
``` 