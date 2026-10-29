# CLAUDE.md

<!-- Replace with one line: what the app is and who it is for. HTML comments are stripped before loading, so unfilled placeholders cost nothing. -->

Code `src/` · Design `design/` · Plan `plans/` · Reference `ref/` · History `buildlogs/`.

## Environment
<!-- Delete lines that do not apply. -->
- The user runs installs, servers, tests, builds and migrations. Claude writes code and gives exact commands.
- The user commits and pushes. Claude never commits.

## Workflow
User commands: `/triage`, `/phase N`, `/save-context`.
- New session: read plans/README.md, the current phase's Resume point, design/ARCHITECTURE.md. Nothing else until a task needs it.
- Near the session limit, read .claude/skills/save-context/SKILL.md and follow it without being asked.
- Phase size: one phase = one session (~100k tokens), one layer or feature slice, ~15 to 25 files.

## Context rules
- Grep or Glob first, then Read only the matching range (offset, limit). Never read a whole large file to find one part.
- Searches spanning many files, docs fetching and long logs go to a subagent; take back only its summary.
- ref/error.md: Grep for the first error line and read around it. Read the whole file only if that finds nothing. Name the failing line before proposing a fix.
- Read buildlogs/ and plans/done/ only when the user asks.

## Rules
- YAGNI: build only what the current task needs. No speculative abstractions, options, config or docs.
- Docs record what code and git cannot. Never restate the code.

## Compact instructions
Keep: current phase and task, files changed this session, unresolved errors, decisions made. Drop: file contents already written, resolved errors.
