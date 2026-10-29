---
name: triage
description: Triage START.md into phases
disable-model-invocation: true
---

Triage START.md into phases. Write no code.

1. Read START.md and plans/README.md. Read only the phase READMEs and ref/ files the tasks touch.
2. Each task goes into an existing phase or a new phase. Put each open question under Open questions in the first phase it affects. Order phases by dependency so nothing is redone later. Respect phase size; add phases instead of growing one.
3. Copy each task verbatim under Requested, then break it into Tasks. Renumber later phases if you insert one.
4. Append decisions to ref/decisions.md as `YYYY-MM-DD: <decision> (<why>)`. Never rewrite old lines.
5. Update the table in plans/README.md. Clear START.md down to its header line.
6. Reply with the phase breakdown. Ask now only questions that change the phase order; the rest wait for their phase. Do not ask what ref/decisions.md already answers.

Phase README (`plans/phase-NN-<slug>/README.md`). Add a section only when the phase needs it:

````md
# Phase NN: <name>
Status: Planned
Depends on: <phases or none>
Goal: <one sentence>
Refs: <ref/ files to read, or none>

## Requested
<verbatim from START.md>

## Open questions
- [ ] <question; omit section if none>

## Tasks
- [ ] <task>

## Verify
<commands the user runs>

## Resume point
<where work stopped, next step, decisions not to redo>
````
