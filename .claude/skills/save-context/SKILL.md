---
name: save-context
description: Save session state before the user clears the session
disable-model-invocation: true
---

Save state so the next session can resume from files alone.

1. Current phase README: tick finished tasks, rewrite Resume point (where work stopped, next step, decisions not to redo). If the phase overran, move the remaining tasks into a new phase right after it.
2. Update the table in plans/README.md.
3. Update only the design/ files this session made wrong:

| File | Update when |
|---|---|
| ARCHITECTURE.md | A module, entry point, route or job is added or moved |
| DATAFLOW.md | A model, store or integration changes |
| SECURITY.md | Auth, permissions, trust boundaries or secret handling change |
| UI.md | A token or shared component changes |
| UX.md | A screen or flow is added or changed |

4. Write `buildlogs/YYYY-MM-DD-<2 to 5 word slug>.md` (unique per day). Skip if the session only made trivial changes. 10 to 30 lines, no secrets or customer data (this folder is committed):

````md
# <Title>
Date: YYYY-MM-DD · Phase: NN

## Why
<problem or requirement>

## Changed
- path: one line

## Gotchas
<not obvious from the diff; omit if none>
````

5. Reply with one line: what to type to resume, e.g. `/phase 3`.
