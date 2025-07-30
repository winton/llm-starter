# start.md — Agentic System Bootstrap

Drop this file into your LLM chat. It defines how to discover agents, track state, and route work.

## Directory Layout

```text
llm/
  agents/     # agent prompts
  ledgers/    # state, tasks, configs
  agents.md   # agent list
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
| **summary** | ≤1-line description or mission.                                        |
| **refs**    | Related files, URLs, agent IDs (comma-separated).                      |
| **status**  | Generic field for maintaining state (may be updated).                  |

> Use only the keys that add value for the entry. Everything else goes in the body.

## Agent File (`agents/<agent-id>.md`)

```markdown
# doc-sync
- schema: agent
- summary: keep code & docs identical

Review and update `docs/`, ensuring that it serves as a mirror to the code.
```

## Ledger File (`ledgers/*.md`)

```markdown
# password-reset-flow
- schema: task
- summary: document password reset flow
- refs: auth/user.ts:77-110, docs/api.md
- status: incomplete

Supports password resets via both email and SMS tokens.

# session-token-strategy
- schema: decision
- summary: use JWT for session tokens
- refs: auth/session.ts:45-67, docs/api.md
- status: complete

Chose JWT over DB-backed sessions to reduce load and simplify horizontal scaling.
```

> Ledgers consist of one or more appended Markdown Objects.

> Consult the `ledger-writer` agent before writing to the ledger.