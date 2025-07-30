# start.md — Agentic System Bootstrap (drag into your preferred LLM IDE)

> Drop this file into your preferred LLM IDE as the entrypoint. It describes the project layout and metadata schema so the LLM can retrieve available agents and automatically route your request to the most suitable agent.

## Directory Layout

```text
llm/
  agents/     # agent prompts
  ledgers/    # state/context
  yaml/       # non-append configuration
  start.md    # entrypoint
```

## Markdown Object Schema

Every object follows the same skeleton:

```markdown
# <agent-id>              # agent id header (required)
- key: value              # metadata list (≥1 line, optional)
- key: value
...

<Markdown body>           # free-form until next 1st-level heading
```

## Agent Prompt File (`agents/<agent-id>.md`)

| key | required | description |
|-----|----------|-------------|
| scope | yes | mission statement |
| input | optional | input types |
| call | optional | downstream agent IDs (omit or 'none' if no calls) |
| ledger | yes | ledger namespaces |
| yaml | yes | yaml namespaces |

**Example**

```markdown
# doc-sync
- scope: keep code & docs identical
- input: diff | path
- call: test-guardian, planner
- ledger: global, doc-sync
- yaml: doc-sync

Review and update `docs/`, ensuring that it serves as a mirror to the code.
```

## Ledger File (`ledgers/<global|agent-id|*>.md`)

Contains multiple Markdown Object Schema entries (append-only) for state/context tracking.
Ledger entries must follow the Markdown Object Schema above, focusing on recording completed work, suggested next tasks, important decisions, and useful information.

| key | required | description |
|-----|----------|-------------|
| schema | yes | `Info`, `Feature`, `Decision`, `Task`, `Anchor` |
| summary | yes | ≤1-line description |
| refs | yes | files or URLs (comma list) |
| next | no | suggested follow-up work |

**Example**

```markdown
# doc-sync
- schema: Task
- summary: password reset flow
- refs: auth/user.ts:77-110
- next: add nil-user-id test

Supports password resets via both email and SMS tokens.

# doc-sync
- schema: Decision
- summary: use JWT for session tokens
- refs: auth/session.ts:45-67, auth/config.ts:12-15, docs/api.md
- next: implement refresh token rotation

Chose JWT over database sessions for better scalability.
```

## YAML File (`yaml/*.yaml`)

The YAML directory is for non-append configuration at the discretion of the agent.

## Post-Execution
- After completing an action, provide a concise summary of the work performed.
- Review any ledger entries for defined `next` fields.
- Propose the upcoming tasks by referencing those `next` values.