---
name: phase
description: Build phase N from plans/
argument-hint: "[phase-number]"
disable-model-invocation: true
---

Build phase $0, or mark it verified if the user says it passed.

## Build
1. Read the phase $0 README, `plans/phase-NN-*/README.md` with NN zero padded (Resume point first), design/ARCHITECTURE.md, and only the files under Refs.
2. If the README has Open questions, ask them all in one message and stop. Log answers in ref/decisions.md, tick them, then continue.
3. Build every task without stopping. Ask only on real blockers (data loss, conflicting requirements). List judgment calls in the reply.
4. Tick tasks as they land. Update design/ARCHITECTURE.md when a module, route or job is added or moved.
5. End with a Verify block. Write it to ref/commands.md as a checkbox list, replacing the old one. Set Status to Built (awaiting verify).

## Verified
When the user confirms: Status Done, move the folder to plans/done/, update plans/README.md, then run the save-context steps.
