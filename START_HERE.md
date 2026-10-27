# Start Here - openclaw-workspace

A git snapshot of an OpenClaw agent workspace: the folder OpenClaw treats
as an agent's home (its working directory and the Markdown files loaded
into each session as startup context). There is no application code here,
only the starter files OpenClaw seeds into a brand-new workspace. Nothing
in this repository is OpenClaw itself -- OpenClaw is a separate project (a
gateway plus an `openclaw` CLI for running chat-connected agents).

## Status: dormant, unfilled template

The README records that the repo began with a 2026-03-28 checkpoint, that
the README is the second commit on the branch, and that it has no tests
and no CI. The content is an unfilled template, not a configured agent:

- `IDENTITY.md` and `USER.md` still hold their fill-in-the-blank
  placeholders.
- `HEARTBEAT.md` is empty apart from comments.
- `BOOTSTRAP.md` is still present. By its own instructions it is deleted
  once the first-run conversation is finished, so this snapshot looks like
  it was taken before that happened.
- `AGENTS.md` refers to `memory/YYYY-MM-DD.md` and `MEMORY.md`. Neither
  exists in this repository.

It also predates the current OpenClaw layout. `.openclaw/workspace-state.json`
records a seed date of 2026-02-16. Per the README (checked against OpenClaw
release 2026.9.7), that file is legacy, `HEARTBEAT.md` and `TOOLS.md` are
retired (local tool notes now live in a `## Tools` section of `AGENTS.md`),
and `openclaw doctor --fix` is the migration path. Running it would migrate
the retired files described above; review the resulting diff before
committing it.

## Layout

| Path | What it is |
|------|------------|
| `AGENTS.md` | Operating instructions: session startup order, memory conventions, safety rules, group-chat etiquette, heartbeat guidance. |
| `SOUL.md` | Persona, tone and boundaries for the agent. |
| `IDENTITY.md` | Name, creature, vibe, emoji, avatar. Blank template. |
| `USER.md` | Notes about the person the agent helps. Blank template. |
| `BOOTSTRAP.md` | One-time first-run script ("figure out who you are"). |
| `HEARTBEAT.md` | Checklist for periodic check-ins. Empty. |
| `TOOLS.md` | Space for local environment notes. Contains only examples. |
| `.openclaw/workspace-state.json` | Seed marker written by OpenClaw (`version` and `bootstrapSeededAt`). |

## Quick start

There is nothing to build or install. To point an OpenClaw agent at this
folder (command checked by the README against `openclaw agents add --help`,
OpenClaw 2026.9.7; not run end-to-end against this repository):

```sh
git clone https://github.com/GSV-Sublime-Optimization/openclaw-workspace.git
openclaw agents add my-agent --workspace ./openclaw-workspace
```

Per OpenClaw's docs, the default workspace is `~/.openclaw/workspace`,
changeable with `agents.defaults.workspace` in `openclaw.json` or with the
`OPENCLAW_WORKSPACE_DIR` environment variable. Those settings are taken
from the docs and not verified here (README caveat, preserved).

## Keep personal data out of this repo

OpenClaw's docs recommend keeping a workspace in a private git repository,
because a filled-in workspace is the agent's memory. This repository is
public and currently holds only unfilled templates. Do not commit a
completed `USER.md`, `MEMORY.md`, daily `memory/` notes, or anything
credential-like here unless the repository is made private first. The docs
also list what lives outside the workspace and should never be committed:
`openclaw.json`, credentials, and session data under `~/.openclaw/`.

## Tests

None. The repo is Markdown and JSON files with no code to test and no CI
workflow. There is no build to run and no gate to pass; the check for a
change here is that the files still say only what is true about the
workspace they describe.

## First steps

1. Read `README.md` (status, layout, privacy warning, docs links).
2. Read `AGENTS.md` (session startup order: `SOUL.md`, then `USER.md`,
   then today's and yesterday's daily notes, plus `MEMORY.md` in a main
   session).
3. If you intend to use this workspace with a current OpenClaw release,
   decide on the `openclaw doctor --fix` migration first and review its
   diff before committing anything.
