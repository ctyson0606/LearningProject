# STATE

> Last updated: 2026-09-26

Current working state. Superseded content is deleted, not archived.
For durable rules see METHOD.md.

## Current Focus

Build `template/`: a copy-to-adopt learning-project template that works like a
local claude.ai Project, readable and writable by Claude Code, OpenCode and
DeepSeek Harness, so that switching agents by hand (e.g. when the Claude quota
runs out) loses no context. Spec approved 2026-09-26.

### Problem
Each new subject to learn needs a local space holding the material, the
conversation history and the memory. Every agent keeps its own history where
the others cannot read it, so a new agent starts with no idea where the
learning stands.

### Usage
Copy the contents of `template/` into a new folder, put material into
`materials/sources/`, start any agent there. That is "creating a Project".
Switching projects is opening another folder.

### Structure (data contract)
```
template/
  AGENTS.md            Setup state, topic, long-term goal, learner level,
                       default method and checking style, human-facing
                       language, sources overview, rules for every agent
  CLAUDE.md            "@AGENTS.md" only (Claude Code). OpenCode and DeepSeek
                       Harness read AGENTS.md directly.
  materials/
    sources/           The learner's originals
    generated/         What agents produce and revise (human-facing)
  memory/
    handoff.md         Current state: where learning stands, next step,
                       current mode (+ absolute deadline date), last agent, time
    progress.md        What the learner understands and where they struggle
    decisions.md       Decisions and their reasons
    todo.md            To-dos
    sessions/          One summary per conversation:
                       YYYY-MM-DD-HHMM-<agent>.md
```

### Setup flow (first start, while AGENTS.md is still unset)
The agent reads `materials/sources/`, then asks, skipping anything the sources
already answer, two or three questions at a time:
1. Language for human-facing content (asked first; later questions use it)
2. Long-term goal: exam-oriented (possibly from zero) / genuine understanding /
   exam + full understanding / other (free text). If an exam is involved, its date.
3. Current level
4. Preferred method: explain first / exercises first / guiding questions /
   project-based
5. How understanding is checked: quizzes / exercises / explain it back / none
Then it writes AGENTS.md. After setup, AGENTS.md changes only on request
(e.g. new material added).

### Modes (current state, stored in handoff.md)
- normal: follow the long-term goal and the defaults in AGENTS.md
- sprint: e.g. "exam in 3 days". High-yield exam content only, no deep
  tangents, many exercises
- practice: no new material; set, mark and explain exercises
- more added when needed
The learner switches mode with one sentence. Relative deadlines are stored as
absolute dates. Once the deadline passes, the agent asks whether to return to
normal. Mode overrides the default method and checking style.

### Update rules
| Content | How |
|---|---|
| AGENTS.md | Written by the agent during setup; afterwards only on request |
| handoff.md, sessions/, progress.md, decisions.md, todo.md | Automatic, whenever state actually changes |
| "handoff" command | Optional; flushes the last stretch before a switch |
| materials/generated/ | On request |
| materials/sources/ | Only when the learner names a specific file |

### Language
AI-facing content is English. Human-facing content uses the language asked
for once during setup and recorded in AGENTS.md.

### Non-goals
Quota detection, automatic switching, routing, UI, a multi-project manager,
importing claude.ai Projects, syncing raw transcripts, searching or indexing
material, an adopt script, detecting new material automatically.

### Acceptance (each item run with the real agent; nothing counts unrun)
1. Copy template to an empty folder, add one file to sources/, start Claude
   Code: it enters setup, asks language first, writes AGENTS.md.
2. Keep learning without saying anything about memory: handoff.md and
   sessions/ get updated.
3. Close Claude Code without a handoff, open OpenCode: it states topic, where
   learning stands, recent discussion, next step.
4. Same as 3 with DeepSeek Harness.
5. Reverse direction (OpenCode -> Claude Code) passes.
6. After a switch, the new agent does not ask for the language again; the
   current mode and deadline carry over.
7. Nothing in sources/ is modified at any point.

## Next Steps
1. Install OpenCode and DeepSeek Harness (neither is installed on this machine
   as of 2026-09-26).
2. Run acceptance 1-7 with the real agents. Also confirm the template guard
   holds for OpenCode and DeepSeek Harness inside this repo; only Claude Code
   has been probed.

## Open Questions

## Known Annoyances

## Recent Decisions
- template/AGENTS.md opens with a guard ("ignore if this sits in template/
  under a folder with its own AGENTS.md") instead of storing the entry files
  under other names: both Claude Code (probed) and DeepSeek Harness (source)
  load nested instruction files while this repo edits template/, and renaming
  would break "adopt = copy". Two fresh Claude Code runs in this repo loaded
  the template files and did not act on them.
- Entry files are AGENTS.md plus a CLAUDE.md stub, no DeepSeek-specific file:
  DeepSeek Harness loads every existing AGENTS.md and CLAUDE.md by default and
  does not resolve "@file" imports (read in source,
  packages/context/agent-instructions/src/config.ts, commit 477b4f4).
- Memory files update automatically rather than only on "handoff": the Claude
  quota can run out mid-conversation, after which the agent cannot be asked
  to hand off.
- materials/ is split into sources/ and generated/: a copied template may have
  no git, so an overwritten original could not be recovered.
- Learner notes split: memory/progress.md (AI-facing, terse) vs review notes
  generated on request into materials/generated/ (human-facing).
- Environment facts set to "none": the deliverable is Markdown only, with no
  code to install, build, lint or test; acceptance is manual runs with the
  real agents.
