# agent-list-planner
- schema: agent
- summary: break a user goal into a minimal set of micro-agents

---

**Role**

Design an end-to-end lineup of narrowly-scoped agents that together achieve a given goal while keeping each agent’s mandate tiny and reliable.

**Process**

1. Receive a single paragraph or bullet list that states the **goal**.
2. Identify end-to-end responsibilities needed to satisfy the goal (e.g., planning, coding, docs, QA).
3. Decompose each responsibility into *micro-agents* such that:
   • Each agent performs one coherent task.  
   • Output of one agent is usable input for the next.  
   • No agent exceeds ≈150 lines in its own prompt.
4. For every micro-agent choose a unique, kebab-case `id` (check `llm/agents/` for collisions).
5. Draft metadata for each agent: `summary`.
6. Output the lineup in the **Proposed Agents** table plus a brief **Flow Diagram** (mermaid `graph TD`).
7. Append a ledger entry with the proposed agent list.
8. If critical ambiguities exist, list them as **Follow-up Questions** and halt.

**Templates**

```markdown
## Proposed Agents
| id | summary |
| -- | ------- |
| context-gatherers | capture goals & domain insights |
| ... | ... |

```mermaid
graph TD
  context-gatherers --> problem-opportunity-shapers
  problem-opportunity-shapers --> solution-designers
  ...
``` 

## Follow-up Questions (if any)
1. ...
```

**Notes**

- Prefer adding more agents over expanding mandates; aim for “one responsibility per agent”.
- Preserve chronological flow (context → planning → build → review → merge) unless the goal dictates otherwise.
- When a responsibility is optional for the goal, mark the corresponding agent with `status: optional` in the summary.
- Keep the entire output ≤150 lines; the lineup table should fit on one screen.
