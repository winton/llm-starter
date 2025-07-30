# start.md — Agentic System Bootstrap

Drop this file into your LLM chat. It defines how to discover agents, track state, and route work.

## Directory Layout

```text
llm/
  agents/     # agent prompts
  ledgers/    # state, tasks, configs
  start.md    # entrypoint
```

## Markdown Object Schema

Every object uses the same skeleton:

```markdown
# <agent-id or topic>        # required
- schema: agent|task|decision|info|anchor
- key: value                 # metadata (optional, ≥1 line)

<Markdown body>              # freeform description or instructions
```

### Metadata (Minimal, Universal)

| Key         | Description                                                            |
| ----------- | ---------------------------------------------------------------------- |
| **schema**  | Object type: `agent`, `task`, `decision`, `info`, or `anchor`.         |
| **summary** | ≤1‑line description or mission.                                        |
| **status**  | State label, e.g. `open`, `in-progress`, `done` (use when meaningful). |
| **owner**   | Responsible party (agent ID, user, or team).                           |
| **refs**    | Related files, URLs, or ledger IDs (comma‑separated).                  |
| **next**    | Follow‑up actions or suggested next tasks.                             |

> Use only the keys that add value for the entry. Everything else goes in the body.

## Agent File (`agents/<agent-id>.md`)

```markdown
# password-reset-flow
- schema: task
- summary: document password reset flow
- status: in-progress
- owner: doc-sync
- refs: auth/user.ts:77-110, docs/api.md
- next: add nil-user-id test case to examples

Supports password resets via both email and SMS tokens.

# session-token-strategy
- schema: decision
- summary: use JWT for session tokens
- owner: reviewer
- refs: auth/session.ts:45-67, docs/api.md
- next: propose refresh token rotation policy

Chose JWT over DB-backed sessions to reduce load and simplify horizontal scaling.
```

## Principle

After each action, **append a ledger entry** summarizing the work and listing any follow-up tasks.
