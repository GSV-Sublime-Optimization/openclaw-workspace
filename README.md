# openclaw-workspace

A git snapshot of an [OpenClaw](https://docs.openclaw.ai) agent workspace: the
folder OpenClaw treats as an agent's home (its working directory and the
Markdown files that get loaded into each session as startup context). There is
no application code here, only the starter files OpenClaw seeds into a brand-new
workspace. It is for the repo owner, who uses it to back up or re-create an
agent's workspace, and for anyone curious what an OpenClaw workspace looks like.

OpenClaw is a separate project (a gateway plus an `openclaw` CLI for running
chat-connected agents). Nothing in this repository is OpenClaw itself.

## Status

Dormant. The repo has a single commit (2026-03-28, "chore: checkpoint local
workspace state"), one branch, no tests and no CI.

The content is an unfilled template, not a configured agent:

- `IDENTITY.md` and `USER.md` still hold their fill-in-the-blank placeholders.
- `HEARTBEAT.md` is empty apart from comments.
- `BOOTSTRAP.md` is still present. By its own instructions it is deleted once
  the first-run conversation is finished, so this snapshot looks like it was
  taken before that happened.

It also predates the current OpenClaw layout. `.openclaw/workspace-state.json`
records a seed date of 2026-02-16. OpenClaw's docs (checked against release
2026.9.7) describe that file as legacy, describe `HEARTBEAT.md` and `TOOLS.md`
as retired (local tool notes now live in a `## Tools` section of `AGENTS.md`),
and point to `openclaw doctor --fix` as the migration path.

## Quick start

There is nothing to build or install. To point an OpenClaw agent at this folder:

```sh
git clone https://github.com/GSV-Sublime-Optimization/openclaw-workspace.git
openclaw agents add my-agent --workspace ./openclaw-workspace
```

`openclaw agents add [name] --workspace <dir>` is checked against
`openclaw agents add --help` (OpenClaw 2026.9.7). It has not been run
end-to-end against this repository.

Per OpenClaw's docs, the default workspace is `~/.openclaw/workspace`, and it
can be changed with `agents.defaults.workspace` in `openclaw.json` or with the
`OPENCLAW_WORKSPACE_DIR` environment variable. Those settings are taken from the
docs and not verified here. Running `openclaw doctor --fix` on this workspace
would migrate the retired files described above; review the resulting diff
before committing it.

## Repo layout

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

`AGENTS.md` refers to `memory/YYYY-MM-DD.md` and `MEMORY.md`. Neither exists in
this repository.

## Keep personal data out of this repo

OpenClaw's docs recommend keeping a workspace in a private git repository,
because a filled-in workspace is the agent's memory. This repository is public
and currently holds only unfilled templates. Do not commit a completed
`USER.md`, `MEMORY.md`, daily `memory/` notes, or anything credential-like here
unless the repository is made private first. The docs also list what lives
outside the workspace and should never be committed: `openclaw.json`,
credentials, and session data under `~/.openclaw/`.

## Tests

None. The repo is eight Markdown and JSON files with no code to test and no CI
workflow.

## Where to read more

- `AGENTS.md` and `SOUL.md` in this repo, for how the agent is meant to behave.
- [Agent workspace](https://docs.openclaw.ai/concepts/agent-workspace): location,
  file map and backup advice.
- [Agent bootstrapping](https://docs.openclaw.ai/start/bootstrapping): what the
  first-run ritual is for.
- [SOUL.md personality guide](https://docs.openclaw.ai/concepts/soul).

## License

No license file is included in this repository.
