# Claude Code Project Template

A project template for building apps with [Claude Code](https://code.claude.com/docs/en/setup.md) in small, planned phases.

It is built for two things:

1. **Fast reasoning.** Claude gets short, clear instructions and only the files it needs.
2. **Low token use.** Workflow instructions load only when you call them, so every message stays small.

## How it works

You describe your app in one markdown file. Claude splits the work into **phases**. Each phase fits in one Claude session. You build one phase, check it works, save, clear the session, and start the next one.

```
Describe app  →  /triage  →  /phase 1  →  verify  →  /save-context  →  /clear  →  /phase 2 ...
```

## Requirements

- Claude Code installed ([setup guide](https://code.claude.com/docs/en/setup.md))
- Git

## Setup

### 1. Write your app spec

Open Claude (claude.ai or any chat) and ask it to write a detailed spec for your app. Example prompt:

```
I want to build <your app idea>. Ask me questions one at a time until you
understand it, then write a detailed markdown spec covering: purpose, users,
features, screens, data, tech stack, and security needs.
```

Save the result as a `.md` file, for example `my-app-spec.md`.

### 2. Clone this template

```bash
git clone https://github.com/<your-username>/<this-repo>.git my-app
cd my-app
```

Start a fresh git history so your project does not inherit this template's commits:

```bash
# macOS / Linux
rm -rf .git && git init

# Windows PowerShell
Remove-Item -Recurse -Force .git; git init
```

### 3. Add your spec

Move your spec file into the `ref/` folder:

```
ref/my-app-spec.md
```

### 4. Plan the project

Open `START.md` and write:

```
Prepare my project using the .md file in the ref folder and create all the
plans needed for the project. If there are open questions, address them at
the phase they affect.
```

Launch Claude Code in the project root and run:

```
/triage
```

Claude reads your spec, creates the phases in `plans/`, and clears `START.md`. It writes no code yet.

### 5. Build

```
/phase 1
```

If the phase has open questions, Claude asks them first. Then it builds the whole phase and ends with a **Verify** list of commands to run.

Run them. If something fails, paste the output into `ref/error.md` and tell Claude to read it. When everything passes, tell Claude the phase is verified.

### 6. Save and move on

```
/save-context
/clear
/phase 2
```

`/save-context` writes down exactly where work stopped, so the next session picks up from files alone. Repeat steps 5 and 6 until every phase is done.

## Commands

| Command | When | What it does |
|---|---|---|
| `/triage` | After writing in START.md | Turns your tasks into phases |
| `/phase N` | Start or resume a phase | Builds phase N |
| `/save-context` | End of a session | Saves progress, writes a buildlog |
| `/clear` | After saving | Built in. Starts a fresh session |

New ideas later? Write them in `START.md` and run `/triage` again. Claude slots them into the right phase.

## Folders

| Path | What it holds | In git |
|---|---|---|
| `CLAUDE.md` | Rules Claude reads every session | Yes |
| `START.md` | Your untriaged tasks | Yes |
| `src/` | Your app code | Yes |
| `design/` | How the app is built: architecture, data, security, UI, UX | Yes |
| `buildlogs/` | One short note per session on why things changed | Yes |
| `plans/` | Phases and their progress | No |
| `ref/` | Your spec, decisions, error output | No |
| `.claude/skills/` | The `/triage`, `/phase` and `/save-context` workflows | Yes |

## Customize

- **CLAUDE.md:** replace the comment at the top with one line about your app. Edit the Environment section to say who runs tests and builds (you or Claude).
- **src/CLAUDE.md:** add your code rules (style, testing, error handling), one line each.

Comments written as `<!-- ... -->` inside CLAUDE.md files are stripped before Claude reads them, so leftover placeholders cost nothing.

## Tips

- One phase per session. Run `/save-context` and `/clear` between phases, even if there is room left. A fresh session is cheaper and sharper than a long one.
- Use a smaller model (Sonnet) for routine phases and a larger one (Opus) for planning.
- Run `/context` to see what is using your context window.
- Keep instructions out of chat. Anything Claude must remember belongs in a file.

## License

[MIT](LICENSE). Created by Vincent Herrera. Free to use, modify and share; keep the copyright notice in copies of the template itself.